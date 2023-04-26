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
 <a href='command:katapod.loadPage?[{"step":"step1"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
<span class="step-count"> Step 2 of 3</span>
 <a href='command:katapod.loadPage?[{"step":"step3"}]' 
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->
<div class="step-title">Create the <i>videos-by-tag</i> table</div>

✅ Inspect the `videos-by-tag.csv` file that we will import into a new table:
```
cat /workspace/ds201-lab03/data-files/videos-by-tag.csv
```

Notice how this CSV file categorizes the videos using *tags*: `datastax`, `cassandra`, and `cql`.

✅ Start *cqlsh* again and switch to the *killrvideo* keyspace:

<details class="katapod-details">
  <summary>Solution</summary>

```
cqlsh
USE killrvideo;
```

</details>
<br>

✅ Create a new table with name `videos_by_tag` that can store data from file *videos_by_tag.csv*, such that we get one partition for every tag and each partition can have multiple rows with videos. 

<details class="katapod-details">
  <summary>Solution</summary>

```
CREATE TABLE videos_by_tag (
  tag TEXT,
  video_id TIMEUUID,
  added_date TIMESTAMP,
  title TEXT,
  PRIMARY KEY ((tag), video_id)
);
```

</details>
<br>

✅ Use the COPY command to import the `videos-by-tag.csv` data into your new table:
```
COPY videos_by_tag (tag, video_id, added_date, title)
FROM '/workspace/ds201-lab03/data-files/videos-by-tag.csv'
WITH HEADER = TRUE;
```

✅ Retrieve all rows from table *videos_by_tag* and verify that you get 5 rows as expected.

If the table only has 2 rows instead of 5, make sure that the table primary key has enough columns so that it can uniquely identify each row.

You can always execute `DROP TABLE videos_by_tag;` and go back to the previous steps to make any necessary corrections.

```
SELECT * FROM videos_by_tag;
```

<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"step1"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
  <a href='command:katapod.loadPage?[{"step":"step3"}]' 
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>