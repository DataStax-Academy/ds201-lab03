<!-- TOP -->
<div class="top">
  <img class="scenario-academy-logo" src="https://datastax-academy.github.io/katapod-shared-assets/images/ds-academy-2023.svg" />
  <div class="scenario-title-section">
    <span class="scenario-title">Partitions</span>
    <span class="scenario-subtitle">ℹ️ For technical support, please contact us via <a href="mailto:academy@datastax.com">email</a>.</span>
  </div>
</div>

<!-- NAVIGATION -->
<div id="navigation-top" class="navigation-top">
 <a href='command:katapod.loadPage?[{"step":"intro"}]'
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 1 of 2</span>
 <a href='command:katapod.loadPage?[{"step":"step2"}]' 
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->
<div class="step-title">Explore the <em>videos</em> table</div>

Use `nodetool` to verify that Cassandra is running. (You may need to run this command multiple times.)

✅ Verify that Cassandra is running.
```
nodetool status
```

✅ Start 'cqlsh' so you can execute CQL statements:
```
cqlsh
```

✅ Switch to the *killrvideo* keyspace via the `USE` command:

<details class="katapod-details">
  <summary>Solution</summary>

```
USE killrvideo;
```

</details>
<br>

✅ Execute the following command to view information about the *videos* table: 
```
DESCRIBE TABLE videos;
```
**Question:** What is the partition key for the *videos* table?

<details><summary><b>Answer</b></summary>
<p>
The <i>video_id</i> column is the primary key.
</p>
</details>
<br>

**Question:** How many partitions are in the *videos* table?

<details><summary><b>Answer</b></summary>
<p>
One partition for each unique <i>video_id</i>.
</p>
</details>
<br>

---
**Note:** This table has a single row in each partition rather than using partitions to group related rows. This is an anti-pattern!

---
<br>


✅ Execute the following query to see how partition key values are mapped to tokens by the partitioner:
```
SELECT token(video_id), video_id FROM videos;
```

✅ Exit *cqlsh*:
```
quit
```

<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"intro"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
 <a href='command:katapod.loadPage?[{"step":"step2"}]'
    class="btn btn-dark navigation-bottom-right">Next ➡️
  </a>
</div>
