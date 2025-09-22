Interactive COVID-19 Dashboard
Project Overview

This project is an interactive web-based dashboard designed to visualize the Coronavirus (COVID-19) pandemic data. It presents key statistics in an easily digestible format and allows users to explore different facets of the data through dynamic charts and graphs. The primary goal is to provide a clear, at-a-glance understanding of the pandemic's impact using state-wise daily data.

The dashboard is built using Python with the Dash framework, leveraging Plotly for interactive visualizations and Pandas for efficient data manipulation.

Core Technologies Used

Dash: A Python framework for building analytical web applications. It handles the user interface and interactions without needing JavaScript.

Plotly: A graphing library for creating interactive visualizations.

plotly.graph_objs (go): Used for creating fundamental building blocks of figures like Bar and Line charts.

plotly.express (px): Used for creating full figures like Pie charts in a streamlined way.

Pandas: Used for reading the state_wise_daily.csv file into a DataFrame and performing calculations for key metrics.

Bootstrap: A CSS framework for styling the front-end, providing responsive and visually appealing components like cards and grids.

Application Breakdown
1. Data Loading and Initial Processing

Loads state_wise_daily.csv into a Pandas DataFrame.

Calculates four key summary statistics:

Total Cases: Total number of rows in the dataset.

Active Cases: Rows where Status = Confirmed.

Recovered Cases: Rows where Status = Recovered.

Deaths: Rows where Status = Deceased.

2. Dashboard Layout (app.layout)

The user interface is structured using Dash HTML components and organized as follows:

Main Title: Header displaying "coronavirus pandemic".

Summary Cards: A row of four cards showing Total, Active, Recovered, and Deaths, styled with different background colors (bg-danger, bg-info, etc.) for visual distinction.

Interactive Charts Section:

Commodities Graph (Line Chart): Controlled by a dropdown to visualize trends of 'Mask', 'Sanitizer', and 'Oxygen'.

Zone Distribution Graph (Pie Chart): Controlled by a dropdown to show distribution of 'Red Zone', 'Blue Zone', 'Green Zone', and 'Orange Zone'.

State-wise Data Bar Chart: Full-width bar chart controlled by a dropdown to display 'Hospitalized', 'Recovered', or 'Deceased' cases for each state.

3. Interactivity with Callbacks (@app.callback)

Dash callbacks link input components (e.g., dropdowns) to output components (e.g., graphs), updating them dynamically:

update_graph (Bar Chart)

Input: Dropdown with id='picker'.

Output: Figure of the graph with id='bar'.

Logic: Updates the bar chart based on selection ('All', 'Hospitalized', 'Recovered', 'Deceased') for each state.

generate_graph (Line Chart)

Input: Dropdown with id='plot-graph'.

Output: Figure of the graph with id='graph'.

Logic: Displays trends for commodities ('Mask', 'Sanitizer', 'Oxygen') based on user selection.

generate_graph (Pie Chart)

Input: Dropdown with id='my_dropdown'.

Output: Figure of the graph with id='the_graph'.

Logic: Generates a pie chart showing the distribution of the selected zone type across the dataset using Plotly Express.

Usage

Install dependencies:

pip install dash pandas plotly


Run the app:

python app.py


Open the browser at http://127.0.0.1:8050/ to interact with the dashboard.

Dataset

File: state_wise_daily.csv

Description: Contains state-wise daily COVID-19 data, including confirmed, recovered, deceased cases, and zone classification.
