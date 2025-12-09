<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width,initial-scale=1">
  <title>DDL Operators & Data Types — README</title>
  <style>
    :root{--bg:#0f1724;--card:#0b1220;--muted:#9aa4b2;--accent:#7dd3fc;--accent2:#60a5fa}
    body{font-family:Inter, ui-sans-serif, system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial; background:linear-gradient(180deg,#071029 0%,#081827 100%); color:#e6eef6; padding:36px}
    .container{max-width:900px;margin:0 auto;background:linear-gradient(180deg,rgba(255,255,255,0.02),transparent);border:1px solid rgba(255,255,255,0.04);padding:28px;border-radius:12px;box-shadow:0 8px 30px rgba(2,6,23,0.6)}
    h1{font-size:28px;margin:0 0 6px}
    p.lead{color:var(--muted);margin:0 0 18px}
    section{margin-bottom:18px}
    ul{margin:8px 0 0 20px}
    .code{background:#021024;border-radius:8px;padding:12px;font-family:Menlo,Monaco,Consolas,"Liberation Mono",monospace;font-size:13px;color:#cde7ff;overflow:auto}
    .badge{display:inline-block;background:rgba(125,211,252,0.08);color:var(--accent);padding:6px 10px;border-radius:999px;font-weight:600;margin-left:8px}
    .row{display:flex;gap:18px;flex-wrap:wrap}
    .card{flex:1;min-width:240px;background:rgba(255,255,255,0.01);padding:14px;border-radius:10px;border:1px solid rgba(255,255,255,0.02)}
    footer{margin-top:16px;color:var(--muted);font-size:13px}
    a{color:var(--accent2)}
  </style>
</head>
<body>
  <div class="container">
    <header>
      <h1>DDL Operators & Data Types <span class="badge">Quick Guide</span></h1>
      <p class="lead">A concise, friendly README describing basic DDL concepts, data types commonly used for inputs, and core DDL techniques — with small examples you can copy into a SQL console.</p>
    </header>

    <section>
      <h2>What is DDL?</h2>
      <p>DDL stands for <strong>Data Definition Language</strong>. These are SQL commands used to define, modify, and remove database structures such as tables, indexes, and schemas. Think of DDL as the toolkit you use to build and reshape the skeleton of your database.</p>
    </section>

    <section>
      <h2>DDL Operators (used to create and manage tables)</h2>
      <div class="row">
        <div class="card">
          <h3>CREATE</h3>
          <p>Create new tables or other objects.</p>
          <div class="code"><pre><code>-- create a simple table
CREATE TABLE products (
  id INT PRIMARY KEY,
  name VARCHAR(100),
  price DECIMAL(10,2)
);</code></pre></div>
        </div>

        <div class="card">
          <h3>ALTER</h3>
          <p>Change an existing object's structure (add/remove/modify columns).</p>
          <div class="code"><pre><code>-- add a column
ALTER TABLE products
ADD COLUMN stock INT DEFAULT 0;</code></pre></div>
        </div>

        <div class="card">
          <h3>SP_RENAME</h3>
          <p>Vendor-specific stored procedure (popular in SQL Server) to rename objects.</p>
          <div class="code"><pre><code>-- SQL Server example: rename a column
EXEC sp_rename 'products.name', 'product_name', 'COLUMN';</code></pre></div>
        </div>

        <div class="card">
          <h3>TRUNCATE</h3>
          <p>Quickly remove all rows from a table (structure stays intact). Faster than DELETE without WHERE.</p>
          <div class="code"><pre><code>TRUNCATE TABLE products;</code></pre></div>
        </div>

        <div class="card">
          <h3>DROP</h3>
          <p>Completely remove a table or other object from the database.</p>
          <div class="code"><pre><code>DROP TABLE products;</code></pre></div>
        </div>
      </div>
    </section>

    <section>
      <h2>Data Types — what inputs the user is giving to the tool</h2>
      <p>Below are common input types and a short description of when to use each.</p>
      <ul>
        <li><strong>Integer</strong> — whole numbers (e.g., ids, counts). Use <code>INT</code> or variants like <code>SMALLINT</code>.</li>
        <li><strong>Float</strong> — approximate numeric values with fractions. Use <code>FLOAT</code> or <code>DOUBLE</code> (careful with precision).</li>
        <li><strong>String</strong> — text values. Use <code>VARCHAR(n)</code>, <code>TEXT</code>, or vendor-specific types.</li>
        <li><strong>Money</strong> — currency amounts. Use <code>DECIMAL(precision,scale)</code> or a dedicated <code>MONEY</code> type where supported to avoid rounding errors.</li>
      </ul>

      <div class="code" style="margin-top:10px"><pre><code>-- SQL snippet showing data types
CREATE TABLE orders (
  order_id INT PRIMARY KEY,
  customer_name VARCHAR(255),
  total_amount DECIMAL(12,2), -- money-like field
  discount_rate FLOAT
);</code></pre></div>
    </section>

    <section>
      <h2>Techniques of DDL</h2>
      <p>A quick reference listing the core DDL techniques and what they do.</p>
      <ol>
        <li><strong>Create</strong> — define tables, schemas, indexes.</li>
        <li><strong>Alter</strong> — modify existing table/column/index definitions.</li>
        <li><strong>Sp_rename</strong> — rename objects (commonly SQL Server).</li>
        <li><strong>Truncate</strong> — remove all rows fast, keep structure.</li>
        <li><strong>Drop</strong> — delete the table or object permanently.</li>
      </ol>
    </section>

    <section>
      <h2>Best practices & tips</h2>
      <ul>
        <li>Prefer <code>DECIMAL</code>/<code>NUMERIC</code> over <code>FLOAT</code> for money values to avoid precision issues.</li>
        <li>Use migrations (versioned DDL) in production to track schema changes — tools like Flyway, Liquibase, or framework migrations are gold.</li>
        <li>Be careful with <code>DROP</code> and <code>TRUNCATE</code> — they are destructive. Use backups or transactions where possible.</li>
        <li>Test schema changes in a staging environment before applying to production.</li>
      </ul>
    </section>

    <footer>
      <p>Made with ❤️ — drop this file into your repo as <code>README.html</code> or copy sections into a <code>README.md</code> file.</p>
    </footer>
  </div>
</body>
</html>
# SQL
