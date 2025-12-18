# PowerBI-showcase-II
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Power BI Data Transformation Assignment | PL-300</title>
  <style>
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      line-height: 1.6;
      color: #333;
      max-width: 960px;
      margin: 0 auto;
      padding: 2rem 1rem;
      background-color: #fafafa;
    }
    header {
      text-align: center;
      margin-bottom: 2.5rem;
      border-bottom: 1px solid #eee;
      padding-bottom: 1.5rem;
    }
    h1, h2, h3 {
      color: #005a9e;
    }
    h1 {
      font-size: 2.2rem;
      margin-bottom: 0.5rem;
    }
    h2 {
      margin-top: 2rem;
      border-bottom: 1px solid #eee;
      padding-bottom: 0.4rem;
    }
    table {
      width: 100%;
      border-collapse: collapse;
      margin: 1.2rem 0;
    }
    th, td {
      text-align: left;
      padding: 0.75rem;
      border: 1px solid #ddd;
    }
    th {
      background-color: #f4f4f4;
    }
    code {
      background: #f0f0f0;
      padding: 0.2rem 0.4rem;
      border-radius: 4px;
      font-family: Consolas, Monaco, monospace;
    }
    footer {
      margin-top: 3rem;
      text-align: center;
      font-size: 0.9rem;
      color: #666;
      border-top: 1px solid #eee;
      padding-top: 1.5rem;
    }
    a {
      color: #0078d7;
      text-decoration: none;
    }
    a:hover {
      text-decoration: underline;
    }
  </style>
</head>
<body>
  <header>
    <h1>Power BI Data Transformation Assignment</h1>
    <p><strong>Course:</strong> PL-300: Microsoft Power BI Data Analyst<br>
    <strong>Lab:</strong> 02 – Transform Data in Power BI</p>
  </header>

  <section>
    <h2>Overview</h2>
    <p>This assignment demonstrates core data cleansing, transformation, and modeling techniques using <strong>Power Query Editor</strong> in <strong>Power BI Desktop</strong>. The goal is to prepare raw datasets from a SQL Server source and a CSV file into a structured semantic model suitable for business analytics.</p>
    <p>Key skills practiced include:</p>
    <ul>
      <li>Column renaming, filtering, and removal</li>
      <li>Merging and expanding related tables</li>
      <li>Handling missing values with custom logic</li>
      <li>Unpivoting columns and deriving new date fields</li>
      <li>Configuring appropriate data types for analytical integrity</li>
      <li>Managing query load behavior to optimize the data model</li>
    </ul>
  </section>

  <section>
    <h2>Environment</h2>
    <ul>
      <li><strong>Execution Platform:</strong> PL-300 Virtual Lab Environment</li>
      <li><strong>Tool:</strong> Power BI Desktop</li>
      <li><strong>Data Sources:</strong>
        <ul>
          <li>SQL Server (via <code>.pbix</code> starter file)</li>
          <li><code>ColorFormats.csv</code> (included in lab assets)</li>
        </ul>
      </li>
    </ul>
  </section>

  <section>
    <h2>Instructions Summary</h2>
    <ol>
      <li><strong>Download & Setup</strong>
        <ul>
          <li>Download the lab assets from: <a href="https://github.com/MicrosoftLearning/PL-300-Microsoft-Power-BI-Data-Analyst/raw/Main/Allfiles/Labs/02-transform-data-power-bi/02-transform-data.zip" target="_blank">Download ZIP</a></li>
          <li>Extract to: <code>C:\Users\Student\Downloads\02-transform-data</code></li>
          <li>Open <code>02-Starter-Sales Analysis.pbix</code></li>
        </ul>
      </li>
      <li><strong>Transform Queries in Power Query Editor</strong><br>
        Each query was transformed according to business requirements:</li>
    </ol>

    <table>
      <thead>
        <tr>
          <th>Query Name</th>
          <th>Source Table</th>
          <th>Key Transformations</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td><code>Salesperson</code></td>
          <td><code>DimEmployee</code></td>
          <td>Filter <code>SalesPersonFlag = TRUE</code>; merge <code>FirstName</code> + <code>LastName</code>; rename columns (<code>EmployeeID</code>, <code>UPN</code>)</td>
        </tr>
        <tr>
          <td><code>SalespersonRegion</code></td>
          <td><code>DimEmployeeSalesTerritory</code></td>
          <td>Remove surrogate keys; retain only <code>EmployeeKey</code> and <code>SalesTerritoryKey</code></td>
        </tr>
        <tr>
          <td><code>Product</code></td>
          <td><code>DimProduct</code></td>
          <td>Filter <code>FinishedGoodsFlag = TRUE</code>; expand subcategory &amp; category; merge with <code>ColorFormats</code>; rename columns</td>
        </tr>
        <tr>
          <td><code>Reseller</code></td>
          <td><code>DimReseller</code></td>
          <td>Expand geography; standardize <code>BusinessType</code> values (<code>Ware House</code> → <code>Warehouse</code>); rename columns</td>
        </tr>
        <tr>
          <td><code>Region</code></td>
          <td><code>DimSalesTerritory</code></td>
          <td>Exclude <code>SalesTerritoryAlternateKey = 0</code>; rename columns</td>
        </tr>
        <tr>
          <td><code>Sales</code></td>
          <td><code>FactResellerSales</code></td>
          <td>Replace missing <code>TotalProductCost</code> using <code>StandardCost × Quantity</code>; set correct data types (<code>Fixed Decimal</code> for financial fields)</td>
        </tr>
        <tr>
          <td><code>Targets</code></td>
          <td><code>ResellerSalesTargets</code></td>
          <td>Unpivot months (<code>M01–M12</code>); replace hyphens; derive <code>TargetMonth</code> as date; scale <code>Target × 1000</code></td>
        </tr>
        <tr>
          <td><code>ColorFormats</code></td>
          <td><code>ColorFormats.csv</code></td>
          <td>Promote first row to headers; <strong>disabled load</strong> (used only for merging into <code>Product</code>)</td>
        </tr>
      </tbody>
    </table>

    <h3>Final Model</h3>
    <ul>
      <li><strong>8 queries</strong> configured in Power Query</li>
      <li><strong>7 tables</strong> loaded into the semantic model (excluding <code>ColorFormats</code>)</li>
      <li>All column names standardized for clarity and usability</li>
      <li>Data types optimized for aggregation and reporting</li>
    </ul>
  </section>

  <section>
    <h2>Output Validation</h2>
    <p>Upon completing all transformations and selecting <strong>Close & Apply</strong>, the Power BI data model contains the following tables:</p>
    <ul>
      <li><code>Salesperson</code></li>
      <li><code>SalespersonRegion</code></li>
      <li><code>Product</code></li>
      <li><code>Reseller</code></li>
      <li><code>Region</code></li>
      <li><code>Sales</code></li>
      <li><code>Targets</code></li>
    </ul>
    <p>Each table matches the expected row and column counts as specified in the lab instructions.</p>
  </section>

  <section>
    <h2>Notes</h2>
    <ul>
      <li>This assignment adheres strictly to the PL-300 lab guidelines.</li>
      <li>Column names and data types were configured to support intuitive report development and accurate DAX calculations.</li>
      <li>The <code>ColorFormats</code> query is not loaded into the model to avoid redundancy, as its data is already integrated into the <code>Product</code> table via a left-outer merge.</li>
    </ul>
  </section>

  <footer>
    <p>Prepared by: Pang Kah Hwee | December 2025</p>
    <p>
      This work is derived from Microsoft Learn training materials and is used for educational purposes only.<br>
      Original content: <a href="https://learn.microsoft.com/training/" target="_blank">Microsoft Learn – PL-300</a>
    </p>
  </footer>
</body>
</html>
