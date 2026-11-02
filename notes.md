# Pool schedules: notes

# 02112026 Step 0, morning session, took about 1.5 hours.

- Done: Set up github auth, git global config, 2FA, uv, Code, empty repo

- Repo: git@github.com:CaroG/pool-schedules.git

- Next time: uv init pool-schedules, first push, DevTools on first pool site

# 02112026  afternoon session, exploration

- Decided on aggregating Utrecht pools. Amsterdam already has zwemsterdam.nl, so there is little to add.That page is built with R backend and React frontend. This project is supposed to be a python learning project.

- Utrecht has a site that aggregates the schedules of the 4 public pools. Decided to start with that, and then add regional pools.

- Investigation of https://mijn.zwemmen-utrecht.nl/rooster
It's accessible without login. robots.txt doesn't explicitly prohibit scraping.

- Krommerijn has a different operator in winter, but is listed on zwemmen-utrecht.nl in summer. In winter, itś members oly. The schedule is avilable publicl, but thereś no point adding it if it isn;t accessible to the general public. 

-Note for data structure: One location has several pools (wedstrijd, doelgroepen, buiten) with different schedules, so that needs to be accounted for in the data structure.

- Endpoint URL and its parameters (StartDate, EndDate, WarehouseID, ActivityID).

- Response is JSON, items plus _meta, no pagination, tz-aware timestamps.
 -Quirks: duplicates, per-location rows, whitespace in names.
- Decisions: Krommerijn out (members-only in   winter), no terms found, polite scraping.

- Next time: count distinct (ActivityID, Name) pairs with Counter, then draft the row model and category enum.