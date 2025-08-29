| Column                        | Type      | Description                                                                                                                                                                                                                 | Example Value                                                                                   |
|-------------------------------|-----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------|
| match_id                      | int       | The unique identifier of the match                                                                                                                                                                                          | 3754058                                                                                          |
| match_date                    | date      | The date of the match                                                                                                                                                                                                       | 2016-01-02                                                                                       |
| kick_off                      | time      | The time of the match                                                                                                                                                                                                       | 16:00:00.000                                                                                     |
| competition (*)               | object    | Competition object with `competition_id`, `competition_name`, and `country_name` attributes                                                                                                                                | {"competition_id":2,"country_name":"England","competition_name":"Premier League"}                |
| season                        | object    | Season object with `season_id` and `season_name` attributes                                                                                                                          | {"season_id":27,"season_name":"2015/2016"}                                                       |
| home_team (*)                 | object    | Home team object with `home_team_id`, `home_team_name`, `home_team_gender`, `home_team_group`, `country` (with nested `id` and `name`), and `managers` (list of objects with `id`, `name`, `nickname`, `dob`, `country`)   | {...see below...}                                                                                |
| away_team (*)                 | object    | Away team object with `away_team_id`, `away_team_name`, `away_team_gender`, `away_team_group`, `country` (with nested `id` and `name`), and `managers` (list of objects with `id`, `name`, `nickname`, `dob`, `country`)   | {...see below...}                                                                                |
| home_score                    | int       | The final score of the home team                                                                                                                                                                                            | 0                                                                                                |
| away_score                    | int       | The final score of the away team                                                                                                                                                                                            | 0                                                                                                |
| match_status                  | string    | The current status of collection for this match (e.g., "available", "deleted", "scheduled", "processing")                                                                            | "available"                                                                                      |
| match_status_360 (*)          | string    | The current status of three-sixty data collection for this match                                                                                                                      | "available"                                                                                      |
| last_updated                  | DateTime  | The date and time at which this match information was last updated                                                                                                                    | 2021-10-29T23:44:19.940296                                                                       |
| last_updated_360 (*)          | DateTime  | The date and time at which this match 360 information was last updated                                                                                                                | 2021-06-12T16:17:31.694                                                                          |
| metadata (*)                  | object    | Contains tags detailing the versions of `data_version`, `shot_fidelity_version`, and `xy_fidelity_version`                                                                           | {"data_version":"1.1.0","shot_fidelity_version":"2","xy_fidelity_version":"2"}                   |
| match_week                    | int       | Number corresponding to the weeks into the competition this match is                                                                                                                  | 20                                                                                               |
| competition_stage             | object    | Competition stage object with `id` and `name` attributes                                                                                                                             | {"id":1,"name":"Regular Season"}                                                                 |
| stadium (*)                   | object    | Stadium object with `id`, `name`, and `country` (with nested `id` and `name` attributes)                                                                                             | {"id":20,"name":"King Power Stadium","country":{"id":68,"name":"England"}}                       |
| referee (*)                   | object    | Referee object with `id`, `name`, and `country` (with nested `id` and `name` attributes)                                                                                            | {"id":5,"name":"Andre Marriner","country":{"id":68,"name":"England"}}                            |

<details>
<summary>Example home_team object</summary>

```json
{
  "home_team_id": 22,
  "home_team_name": "Leicester City",
  "home_team_gender": "male",
  "home_team_group": null,
  "country": {
    "id": 68,
    "name": "England"
  },
  "managers": [
    {
      "id": 60,
      "name": "Claudio Ranieri",
      "nickname": null,
      "dob": "1951-10-20",
      "country": {
        "id": 112,
        "name": "Italy"
      }
    }
  ]
}
```
</details>

<details>
<summary>Example away_team object</summary>

```json
{
  "away_team_id": 28,
  "away_team_name": "AFC Bournemouth",
  "away_team_gender": "male",
  "away_team_group": null,
  "country": {
    "id": 68,
    "name": "England"
  },
  "managers": [
    {
      "id": 38,
      "name": "Eddie Howe",
      "nickname": null,
      "dob": "1977-11-29",
      "country": {
        "id": 68,
        "name": "England"
      }
    }
  ]
}