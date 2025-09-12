Project Overview: Interactive COVID-19 Dashboard This project is an interactive web-based dashboard designed to visualize the Coronavirus (COVID-19) pandemic data. It presents key statistics in an easily digestible format and allows users to explore different facets of the data through dynamic charts and graphs. The primary goal is to provide a clear, at-a-glance understanding of the pandemic's impact using state-wise daily data. The dashboard is built using Python with the Dash framework, leveraging Plotly for creating interactive visualizations and Pandas for efficient data manipulation.

Core Technologies Used 
● Dash: A Python framework for building analytical web applications. It's the backbone of this project, enabling the creation of the user interface and handling user interactions without needing to write JavaScript. 
● Plotly (plotly.graph_objs & plotly.express): A graphing library used to create the interactive visualizations. 
○ plotly.graph_objs (go) is used for creating fundamental building blocks of figures like Bar and Line charts. 
○ plotly.express (px) is used for creating entire figures at once, like the Pie chart, in a more streamlined way.
● Pandas: A powerful data analysis and manipulation library. It's used here to read the state_wise_daily.csv file into a DataFrame and perform calculations to get key metrics. 
● Bootstrap: A popular CSS framework used for styling the front-end. It provides pre-built components (like cards and grids) to make the dashboard responsive and visually appealing with minimal custom styling. Application Breakdown 1. Data Loading and Initial Processing 
● The application starts by loading the dataset state_wise_daily.csv into a Pandas DataFrame.
● It then calculates four key summary statistics from this data: ○ Total Cases: The total number of rows in the dataset. 
○ Active Cases: The count of rows where the 'Status' column is 'Confirmed'. 
○ Recovered Cases: The count of rows where the 'Status' is 'Recovered 2. Dashboard Layout (app.layout) The user interface is structured using Dash HTML components, which are Python wrappers for HTML elements. The layout is organized as follows: 
● Main Title: A header displaying "cororna virus pandemic". 
● Summary Cards: A row of four cards, each displaying one of the key statistics (Total, Active, Recovered, Deaths). These cards are styled with different background colors (bg-danger, bg-info, etc.) for visual distinction. 
● Interactive Charts Section: ○ A row containing two graphs side-by-side: 1. Commodities Graph: A line chart controlled by a dropdown to visualize data related to 'Mask', 'Sanitizer', and 'Oxygen'. 2. Zone Distribution Graph: A pie chart controlled by a dropdown to show the distribution of 'Red Zone', 'Blue Zone', 'Green Zone', and 'Orange Zone'. ○ A final row with a full-width bar chart. 3. State-wise Data Bar Chart: This chart is controlled by a dropdown to display 'Hospitalized', 'Recovered', or 'Deceased' cases for each state.
3. Interactivity with Callbacks (@app.callback) The dashboard's dynamic nature comes from three callback functions. A callback function in Dash links an Input component (like a dropdown) to an Output component (like a graph). Whenever the value of the input changes, the callback function is automatically executed, and the output is updated.
1. update_graph (Bar Chart): ○ Input: The value from the dropdown with id='picker'. ○ Output: The figure of the graph with id='bar'. ○ Logic: It checks the selected value ('All', 'Hospitalized', 'Recovered', 'Deceased') and updates the bar chart to show the corresponding data for each state. 2. generate_graph (Line Chart): ○ Input: The value from the dropdown with id='plot-graph'. ○ Output: The figure of the graph with id='graph'.
2. ○ Logic: It updates the line chart to display trends for different commodities ('Mask', 'Sanitizer', 'Oxygen') based on the user's selection. 3. generate_graph (Pie Chart):
○ Input: The value from the dropdown with id='my_dropdown'.
○ Output: The figure of the graph with id='the_graph'.
○ Logic: It uses plotly.express to generate a pie chart showing the distribution of the
selected zone type across the dataset
