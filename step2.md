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
<span class="step-count"> Step 2 of 2</span>
</div>

<!-- CONTENT -->

<div class="step-title">Create the <i>videos-by-tag</i> table</div>

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus eget purus faucibus, consequat tortor a, feugiat diam. Fusce at tortor sagittis, gravida dolor sed, sollicitudin arcu. Nullam id dolor facilisis, elementum justo a, lobortis justo. Donec lacus magna, ultricies et urna at, congue imperdiet tortor. Vestibulum pulvinar, orci nec bibendum tincidunt, sapien ligula aliquet est, fringilla dictum ex sem vitae ligula. Ut et ultrices ante. Nulla egestas augue erat, vitae volutpat sem porttitor a. Donec ut ligula nulla. Nulla facilisi.

✅ Inspect the `videos-by-tag.csv` file that we will import into a new table:
```
cat /workspace/ds201-lab03/data-files/videos-by-tag.csv
```

Notice how this CSV file categorizes the videos using *tags*: `datastax`, `cassandra`, and `cql`.

✅ Start *cqlsh* again and switch to the *killrvideo* keyspace:
```
/workspace/ds201-lab03/apache-cassandra-4.1.0/bin/cqlsh
USE killrvideo;
```

✅ Create a new table with name `videos_by_tag` that can store data from file *videos_by_tag.csv*, such that we get one partition for every tag and each partition can have multiple rows with videos. 
```
CREATE TABLE videos_by_tag (
  tag TEXT,
  video_id TIMEUUID,
  added_date TIMESTAMP,
  title TEXT,
  PRIMARY KEY ((tag), video_id)
);
```

✅ Use the COPY command to import the `videos-by-tag.csv` data into your new table:
```
COPY videos_by_tag (tag, video_id, added_date, title)
FROM '/workspace/ds201-lab03/data-files/videos-by-tag.csv'
WITH HEADER = TRUE;
```

✅ Retrieve all rows from table *videos_by_tag* and verify that you get 4 rows as expected.
```
SELECT * FROM videos_by_tag;
```

<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"step1"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
</div>