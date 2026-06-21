# PINN-Landslide-Monitor-A-Web-GIS-dashboard-bound-by-laws-of-physics-to-predict-slope-stability
USGS DEM terrain data fused with Open-Meteo rainfall and vegetation metrics. By spatial-matching these features with historical global landslide records, we built a unified dataset to train a Physics-Informed Neural Network (PINN). This powers a Web-GIS app predicting slope stability to foster regional disaster sustainability.

# Problem Statement
Mountainous regions like West Arunachal Pradesh are highly vulnerable to catastrophic landslides triggered by heavy monsoon rains and environmental degradation. Traditional geological models require massive amounts of field data and complex mathematics, making real-time forecasting incredibly difficult. On the other hand, standard AI models often make "unphysical" guesses because they do not inherently understand gravity.

Compounding this problem, there is currently an absolute absence of any operational predictive hazard models tailored specifically for these remote Himalayan corridors. This creates a critical, dangerous gap in reliable, real-time early warning systems required to protect vulnerable local communities and save lives.

# This project bridges the gap between deep learning and physics. By injecting geotechnical engineering principles directly into an AI, we created a smart system that understands terrain limits. It provides an interactive web dashboard where engineers or local authorities can input coordinates or environmental conditions to get an immediate, physics-verified hazard assessment, acting as a scalable tool for disaster risk reduction.

# Project Overview
The PINN Landslide Monitor is an innovative Web-GIS hazard monitoring system designed specifically for the rugged terrain of West Arunachal Pradesh. This project bridges the gap between deep learning and classical geomechanics by embedding the laws of physics—like gravity, shear strength, and friction—directly into an artificial intelligence framework.

By utilizing a Physics-Informed Neural Network (PINN) trained on real-world terrain and weather parameters, the platform calculates a real-time Factor of Safety (FOS) score for any coordinate. Integrated into a sleek, accessible Streamlit web application, it transforms complex satellite data into an actionable early-warning tool to enhance regional climate resilience and disaster sustainability.

# Methodology
Step 1: Geospatial Baseline & Boundary Filtering
The project started by downloading Digital Elevation Model (DEM) map files from the USGS to analyze the height and slope angles of the terrain. Next, a historical global landslide dataset was sourced from Kaggle. Using a coordinate bounding box, the global data was filtered down to extract only the actual landslide cases that occurred inside the project's specific DEM map boundaries.

Step 2: Environmental Feature Integration & Data Balancing
To simulate realistic environmental triggers, dynamic climate and ecological parameters were integrated from Open-Meteo:
Rainfall Depth: Sourced from historical weather records to match heavy monsoon cloudburst stresses.
Vegetation Cover (NDVI): Sourced to factor in how well root systems anchor the soil structure and prevent erosion.
Because the historical Kaggle dataset only contained points where landslides did happen (positive labels), the data was naturally heavily skewed. To fix this, synthetic "stable slope" data (negative labels) was mathematically generated for flat, low-risk geographical areas. This gave the AI a perfectly balanced view of safety versus hazard. All of these layers were matched up and merged into a clean master dataset.csv file.

Step 3: Neural Network Training (The PINN)
Using the compiled dataset, a Physics-Informed Neural Network (PINN) was built and trained in PyTorch. Unlike standard networks, this model optimizes a split loss function: it learns from the historical data points, but is heavily penalized if it violates gravity rules (e.g., predicting a steep, barren cliff under heavy rain as "safe"). The model outputs a geotechnical Factor of Safety (FOS) score.

Step 4: Web Deployment
Finally, the trained PyTorch assets were deployed into a live, interactive webpage using Streamlit and Folium maps. Users can visually click anywhere on the West Arunachal map or manually type in coordinates to observe live hazard updates.

# Technologies Used
1. Core Language: Python
2. Deep Learning Framework: PyTorch (torch, nn)
3. Web Interface & Mapping: Streamlit, Folium, streamlit_folium
4. Data Science & Geospatial Math: NumPy, Pandas, Scikit-Learn
5. Geospatial & Climate Sources: USGS EarthExplorer, Open-Meteo API, kaggle

# Disclaimer:
While the model currently reports a perfect 100% accuracy on our test partition, this is a result of training and validating on a highly targeted, localized, and clean dataset. In real-world complex geomorphic applications, minor noise can alter results, which is why further regional generalization is required.
# Results & Discussion
The system successfully differentiates stable valley grounds from high-risk escarpments. The generated verification curves show that the PINN strictly honors physical boundaries—forcing the Factor of Safety below $1.0$ (unstable) whenever steep slopes encounter extreme rainfall thresholds.

This framework aligns directly with global sustainable development goals (SDGs)—specifically Sustainable Cities and Communities (SDG 11) and Climate Action (SDG 13). Providing an accessible, zero-cost web tool to calculate slope failures empowers regional planners to make data-driven infrastructure decisions, safely locate mountain housing, and mitigate risk sustainably.

# Future Work
I am actively working to expand the scope and precision of this project:
1. DEM Merging via QGIS: I plan to use QGIS to stitch together multiple adjacent USGS DEM tiles spanning across a massive corridor of the Himalayas.
2. Dataset Scaling: Merging these maps will unlock a huge chunk of spatial training data, capturing diverse geological formations.
3. UI/UX Optimizations: The webpage will be progressively updated to handle larger data queries, add automated live weather API feeds, and improve real-time rendering.

------------------------------------------------------------------------*------------------------------------------------------------------------------------------
