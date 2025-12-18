# PowerBI-showcase-II

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
  
  <section>
    <h2>Notes</h2>
    <ul>
      <li>This project adheres strictly to the PL-300 lab guidelines.</li>
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
