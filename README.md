https://singlecelldatasimulatoranalyser-ejdvynxehx9wa6buywyu2m.streamlit.app/

# single_cell_data_simulator_analyser

### Overview
The app integrates various data processing and visualization techniques, allowing users to perform normalization, dimensionality reduction, clustering, and statistical testing directly from their browser. It's built with the biologist in mind, providing intuitive controls and real-time feedback on the dataset's complex structure and expression patterns.

### Features
#### Data Simulation:
- **Characteristics of the Simulated Data**
  - **Cell and Patient Information:**
    - The dataset includes data from a hypothetical set of patients, where each patient has samples taken at different timepoints (e.g., "pre" and "post" treatment).
    - The patients are categorized based on their response to treatment, with responses like "Complete Response (CR)" or "Partial Response (PR)" assigned to each patient.
    - Each sample comprises numerous cells, and the total dataset includes thousands of individual cells distributed across multiple patients and timepoints.
  - **Phenotypic Variability:**
    - Cells are classified into different phenotypes or cell types (e.g., "Type1", "Type2", etc.), with each phenotype potentially representing a distinct cell state or biological condition.
    - The distribution of cell types is varied, reflecting the natural diversity found in biological samples.
  - **Protein Expression Levels:**
    - Each cell in the dataset is characterized by the expression levels of numerous proteins. These proteins are the primary variables in the dataset, analogous to gene expression levels in real scRNA-seq data.
    - Protein expression is simulated to include both baseline levels and phenotype-specific variations, creating realistic variability across the dataset.
  - **Spatial Information:**
    - The dataset includes spatial coordinates for each cell, allowing users to explore spatial relationships and patterns in the data.
    - The spatial information can be used to visualize the distribution of cells across different phenotypes or patient groups. Cell density and cell mixing score can be analyzed based on spatial coordinates.
    - Based on spatial information, users can detect margin of the cell clusters (eg: Tumor margin), which in not included in the current version of the app.
    
- **Normalization Settings:**
  - Users can choose a batch key from their dataset for normalization, ensuring that batch effects can be minimized in downstream analyses.
  - Two methods for normalization can be selected, which include logarithmic transformation, z-score standardization, quantile normalization, and a batch-specific normalization.
  - Normalization is applied only upon user request, and the results are immediately available for review.

- **Data Visualization:**
  - **Violin Matrix Dot Plot:** After normalization, users can visualize the expression levels across different phenotypes or batches using violin plots, enhancing their understanding of the data distribution.
  - **PCA (Principal Component Analysis):** Users can select one or more attributes to color the PCA plot, helping to visually assess the data's variance and the impact of different factors.
  - **UMAP (Uniform Manifold Approximation and Projection):** After performing clustering via the Leiden algorithm, UMAP plots can be generated to visualize the data in a reduced two-dimensional space. This feature helps in identifying clusters or groups within the data, with options to color the plot based on various metadata attributes.

- **Dimensionality Reduction and Clustering:**
  - The app allows users to compute PCA and UMAP directly, with settings to adjust the resolution for clustering, providing a nuanced understanding of the data structure.
  - The clustering results can be visualized in UMAP plots, with flexibility in choosing color schemes based on different metadata to highlight the clusters.

- **Statistical Testing:**
  - The Wilcoxon test can be performed to statistically compare expression levels between two selected groups. This is crucial for identifying significant differences in protein expression across conditions or phenotypes.
  - Users can select the groups and the protein or gene of interest for comparison, and results including the test statistic and p-value are displayed.

- **Interactive Exploration:**
  - The app includes interactive elements like sliders, dropdowns, and buttons that allow users to customize analyses and visualizations on the fly.
  - Data insights and plots can be refreshed and regenerated based on user inputs, facilitating a dynamic exploration environment.

### Technical Aspects
- The app leverages Python libraries such as Scanpy for handling single-cell data, Seaborn and Matplotlib for plotting, and SciPy for statistical analysis.
- Streamlit's framework is used to create an intuitive user interface, making complex data analysis accessible to users without requiring coding expertise.
- Data persistence and state management are handled using Streamlit’s session state capabilities, ensuring that user inputs and computed results are retained across interactions.
