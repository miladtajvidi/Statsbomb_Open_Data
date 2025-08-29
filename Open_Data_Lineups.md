Format

| Column    | Type      | Description                                                      |
|-----------|-----------|------------------------------------------------------------------|
| team_id   | int       | The unique identifier for each team                              |
| team_name | string(*) | The name of the team                                             |
| lineup    | array     | An array of players on the team sheet                            |


Lineups Objects

| Column          | Type      | Description                                                                                                                                         |
|-----------------|-----------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
| player_id       | int       | The unique identifier for this player                                                                                                               |
| player_name     | string(*) | The name of the player                                                                                                                              |
| player_nickname | string    | The nickname of the player on the team                                                                                                              |
| jersey_number   | int       | The number on the player's shirt for this match                                                                                                     |
| country         | object    | The player's nationality, a country object with `id` and `name` attributes                                                                         |
| cards (*)       | array     | An array of given cards objects to the player with `time`, `card_type`, `reason`, and `period` attributes                                          |
| positions (*)   | array     | An array of positions objects with `position_id`, `position`, `from`, `to`, `from_period`, `to_period`, `start_reason`,





