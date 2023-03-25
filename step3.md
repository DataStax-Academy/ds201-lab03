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
</div>

<!-- CONTENT -->
<div class="step-title">Run some queries</div>

✅ Retrieve all videos tagged with `cassandra` from table *videos_by_tag*
```
SELECT * FROM videos_by_tag WHERE tag = 'cassandra';
```

✅ Retrieve all videos tagged with `datastax` from table *videos_by_tag*
```
SELECT * FROM videos_by_tag WHERE tag = 'datastax';
```

✅ Retrieve all videos tagged with `cql` from table *videos_by_tag*
```
SELECT * FROM videos_by_tag WHERE tag = 'cql';
```

✅ Finally, retrieve any video titled `Cassandra Query Language` from table *videos_by_tag*.
```
SELECT * FROM videos_by_tag WHERE title = 'Cassandra Query Language';
```
You should see an error something like this:
<hr>
<div style="color:red;">InvalidRequest: Error from server: code=2200 [Invalid query] message="Cannot execute this query as it might involve data filtering and thus may have unpredictable performance. If you want to execute this query despite the performance unpredictability, use ALLOW FILTERING"</div> 
<hr>

✅ 

✅ 

✅ 

<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"step2"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>

</div>