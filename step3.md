<!-- TOP -->
<div class="top">
  <img class="scenario-academy-logo" src="https://datastax-academy.github.io/katapod-shared-assets/images/ds-academy-2023.svg" />
  <div class="scenario-title-section">
    <span class="scenario-title">Partitions</span>
    <span class="scenario-subtitle">ℹ️ For technical support, please contact us via <a href="mailto:academy@datastax.com">email</a>.</span>
  </div>
</div>

<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"step2"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
<span class="step-count"> Step 3 of 3</span>
  <a href='command:katapod.loadPage?[{"step":"finish"}]' 
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->
<div class="step-title">Run some queries</div>

✅ Retrieve all videos tagged with `cassandra` from table *videos_by_tag*

<details class="katapod-details">
  <summary>Solution</summary>

```
SELECT * FROM videos_by_tag WHERE tag = 'cassandra';
```

</details>
<br>

✅ Retrieve all videos tagged with `datastax` from table *videos_by_tag*

<details class="katapod-details">
  <summary>Solution</summary>

```
SELECT * FROM videos_by_tag WHERE tag = 'datastax';
```

</details>
<br>

✅ Retrieve all videos tagged with `cql` from table *videos_by_tag*

<details class="katapod-details">
  <summary>Solution</summary>

```
SELECT * FROM videos_by_tag WHERE tag = 'cql';
```

</details>
<br>

✅ Finally, retrieve any video titled `Cassandra & SSDs` from table *videos_by_tag*.

<details class="katapod-details">
  <summary>Solution</summary>

```
SELECT * FROM videos_by_tag WHERE title = 'Cassandra & SSDs';
```

</details>
<br>

You should see an error something like this. This is expected. Cassandra only allows efficient queries on primary key columns, which for this table doesn’t include the `title` column.
<hr>
<div style="color:red;">InvalidRequest: Error from server: code=2200 [Invalid query] message="Cannot execute this query as it might involve data filtering and thus may have unpredictable performance. If you want to execute this query despite the performance unpredictability, use ALLOW FILTERING"</div> 
<hr>

✅ For now, you can use ALLOW FILTERING to execute this query but should know that <span style="color:red;">this is anti-pattern!!!</span>: the query requires scanning all rows in the table, which is not feasible for real-life large data sets.

<details class="katapod-details">
  <summary>Solution</summary>

```
SELECT * FROM videos_by_tag 
WHERE title = 'Cassandra & SSDs' ALLOW FILTERING;
```

</details>
<br>


<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"step2"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
  <a href='command:katapod.loadPage?[{"step":"finish"}]' 
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>