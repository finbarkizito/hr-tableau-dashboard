# Technical Build Log: HR Analytics Dashboard

## Data Connection and Source Configuration

We generated a synthetic Human Resources dataset using Python with the Faker library and exported the output as a CSV file named `Human Resources.csv`. The dataset was structured to include employee demographics, employment dates, compensation, and performance metrics.

We then connected Tableau Public directly to `Human Resources.csv` with was the dataset and this source.

We validated data types by assigning employee identifiers, names, gender, education, department, job title, and performance rating as strings, while birth date, hire date, and termination date were configured as date fields. Salary was configured as a numeric field, and City and State were assigned geographic roles.

## Field Preparation and Transformations

We can create an organizational hierarchy by nesting Job Title within Department to support drill-down analysis across views. 

From this, we can apply a custom workbook theme using Trebuchet MS and define four custom colors representing background, text, active status, and terminated status. Worksheet shading was set to dark gray and the default view was configured to fit the entire canvas.

## Calculated Fields Created

For these, we can firstly create a Total Hired field using `COUNT([Employee ID])` to serve as the primary headcount measure across all views. This measure was reused for ranking, distributions, and KPI displays.

We defined Total Terminated by checking for non-null termination dates and counting employee IDs, and Total Active by counting employee IDs where termination dates were null. Both fields were converted to Count aggregations.

We calculated Age using a year-level date difference between Birth Date and Today, then grouped Age into bins representing predefined age ranges. These bins were used consistently across demographic charts.

With that, we can then derive the Location using a CASE statement that classified New York as HQ and all other states as Branch, and define Status based on whether Termination Date was null.

We created Percentage Total Hired using a table calculation dividing total hires by the window total, and Highlight Max using a WINDOW_MAX comparison to support conditional formatting. Additional helper fields included Full Name and Length of Hire calculated using Hire Date and Termination Date logic.

## Chart Construction Steps

We created three KPI BAN sheets for Total Hired, Total Active, and Total Terminated using text marks, formatted with centered alignment and a font size of 18 for visual hierarchy.

We built the Hired trend chart by placing Hire Date (Year) on Columns and Total Hired on Rows with a Line mark. A dual axis was created with a second Total Hired measure displayed as an Area mark at 15% opacity, with synchronized axes and zero baselines removed.

We duplicated the Hired trend to create the Terminated trend by replacing the date with Termination Date and the measure with Total Terminated, applying a pink color to distinguish it from hires.

## Department and Location Analysis

We constructed a Department ranking bar chart with Department on Rows and Total Hired on Columns, then added a discrete INDEX calculation to display rank positions. Departments were sorted descending by Total Hired.

WWe can then buildma Location bar chart using Location on Rows and Total Hired on Columns, applying custom colors to differentiate HQ from Branch locations.

We created a map using Longitude and Latitude with State on Detail, applied a dark map style, and added City as a dual-axis circle layer sized by Total Hired to show city-level distribution.

## Demographics and Performance Analysis

We created a Gender donut chart using two MIN(0) axes, with the outer ring colored by Gender and the inner ring displaying Total Hired labels.

We built a heat map for Age Groups versus Education Level using circle marks sized by Total Hired, alongside bar charts showing Age Group and Education distributions independently.

Therefore we can construct a performance correlation heat map with Performance Rating on Columns and Education Level on Rows, computing Percent of Total within each rating band.

## Income Analysis

We built a Gender Pay Gap chart using a dual-axis approach where one axis displayed a line path connecting genders by education level and the second axis displayed gender-specific shapes colored accordingly.

We created an Age versus Salary scatter plot with Average Age on Columns and Average Salary on Rows, added Job Title to Detail, and included reference lines for overall averages.

## Employee Detail Table

We constructed a multi-column employee detail list using AVG(0) placeholder fields to control column layout. Each column was populated with grouped labels representing identity, role, location, compensation, employment status, and tenure.

We can display the Length of Hire as a bar mark to visually encode tenure length alongside textual employee attributes.

## Layout, Containers, and Dashboard Assembly

We set the Summary dashboard to a fixed size of 1400 by 800 and built the structure using a floating horizontal container separating navigation and content areas.

The navigation container on the left used a fixed width and contained image objects for branding, dashboard navigation actions, export buttons, and external links.

The content container on the right was divided into header, overview, demographics, and income sections, with consistent padding, thin dividers, and spacing applied for alignment.

## Detail Dashboard and Interactivity

We duplicated the Summary dashboard to create a Details view and replaced the content area with a filters and list container. Filters were organized into collapsible containers controlled by show and hide buttons.

We embedded supporting charts inside tooltips using Viz-in-Tooltip, enabled Use as Filter actions across summary charts, and added a floating filter panel with dropdown controls for gender, status, location, and year.

## Visual Polish

We designed a custom background layout in Figma incorporating gradients, rounded elements, and glow effects, then exported it as an image and added it to Tableau as a floating background layer.

We sent the background image to the back of the dashboard and removed all container background colors to allow the Figma design to remain visible.
