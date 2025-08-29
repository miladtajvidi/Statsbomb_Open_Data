| Column                        | Type      | Description                                                                                                        |
|-------------------------------|-----------|--------------------------------------------------------------------------------------------------------------------|
| competition_id                | int       | Unique identifier for the competition                                                                              |
| season_id                     | int       | Unique identifier for the season                                                                                   |
| country_name                  | string    | Name of the country                                                                                                |
| competition_name              | string    | Name of the competition                                                                                            |
| competition_gender            | string    | Gender of the competition                                                                                          |
| competition_youth (*)         | bool      | Youth competition?                                                                                                 |
| competition_international (*) | bool      | International competition?                                                                                         |
| season_name                   | string    | Name of the season                                                                                                 |
| match_updated                 | Date Time | The date and time at which a match within this competition and season was last updated.                            |
| match_updated_360 (*)         | Date Time | The date and time at which a match's 360 data was last updated.                                                    |
| match_available_360 (*)       | Date Time | The date and time at which 360 data for a match was made available or updated.                                     |
| match_available               | Date Time | The date and time at which an available match was updated, or a match was made availab (whichever is more recent). |