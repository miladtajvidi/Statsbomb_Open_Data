| column          | type      | children         | Children types | description                                                                                                                      |->       
|-----------------|-----------|------------------|----------------|----------------------------------------------------------------------------------------------------------------------------------|->
| id              | uuid      |                  |                |The unique identifier for each event                                                                                              |->        
| index           | int       |                  |                |Sequence notation for the ordering of events within each match                                                                    |->
| period          | int       |                  |                |The part of the match the timestamp relates to                                                                                    |->
| timestamp       | timestamp |                  |                |Time in the match the event takes place, recorded to the milliseconds                                                             |->
| minute          | int       |                  |                |The minutes on the clock at the time of this event(resets to 45 at half-time, 90 at the start of extra time,etc)                  |->
| second          | int       |                  |                |The seconds part of the timestamp                                                                                                 |->
| type            | object    | id/name          | int/string     |id/name of the event type                                                                                                         |->
| possession      | int       |                  |                |Indicates the current unique possession in the game                                                                               |->
| possession_team | object    | id/name          | int/string     |id/name of the team that started this possession in control of the ball                                                           |->
| play_pattern    | object    | id/name          | int/string     |id/name of the play pattern relevant to this event                                                                                |->
| team            | object    | id/name          | int/string     |id/name of the team this event relates to(team object will only display if the event is tied to a specific team)                  |->
| duration        | decimal   |                  |                |If relevant, the length the event lasted in seconds                                                                               |->
| tactics         | object    | formation/lineup | int/array      |For events of type(Starting XI or Tactical Shift), tactics object is added.(the formation item describes the formation being used)|->

-> | value                                           | value description                                                                             |
-> |-------------------------------------------------|-----------------------------------------------------------------------------------------------|
-> | e.g. 0b483cd2-1d36-49a0-85c2-149a9de553df       |                                                                                               |
-> | e.g. 1 (# of events)                            | {1st Half, 2nd Half, 3rd Period, 4th Period, Penalty Shootout}                                |       
-> | {1,2,3,4,5}                                     |                                                                                               |
-> | e.g. 00:00:00.000                               |                                                                                               |
-> | e.g. 0                                          |                                                                                               |
-> | e.g. 0                                          |                                                                                               |
-> | e.g. {"id" : 35,"name" : "Starting XI" }        | see below                                                                                     |
-> | e.g. 1 (# of unique possessions)                | New possession are triggered after a team demonstrate they've established control of the ball |
-> | e.g. {"id" : 746,"name" : "Manchester City WFC"}|                                                                                               |
-> | e.g. {"id" : 1,"name" : "Regular Play"}         | see below                                                                                     |
-> | e.g. {"id" : 746,"name" : "Manchester City WFC"}|                                                                                               |
-> | e.g. 0.0                                        |                                                                                               |
-> | e.g. see below                                  | e.g. 343 means three defenders, four midfielders and three strikers                           |


                      

<details> <summary>Tactics example value</summary>
{
  "formation": 433,
  "lineup": [
    {
      "player": { "id": 4637, "name": "Ellie Roebuck" },
      "position": { "id": 1, "name": "Goalkeeper" },
      "jersey_number": 26
    },
    {
      "player": { "id": 4649, "name": "Esme Beth Morgan" },
      "position": { "id": 2, "name": "Right Back" },
      "jersey_number": 14
    },
    {
      "player": { "id": 4648, "name": "Abbie McManus" },
      "position": { "id": 3, "name": "Right Center Back" },
      "jersey_number": 23
    },
    {
      "player": { "id": 17524, "name": "Jennifer Patricia Beattie" },
      "position": { "id": 5, "name": "Left Center Back" },
      "jersey_number": 5
    },
    {
      "player": { "id": 4651, "name": "Demi Stokes" },
      "position": { "id": 6, "name": "Left Back" },
      "jersey_number": 3
    },
    {
      "player": { "id": 10172, "name": "Jill Scott" },
      "position": { "id": 13, "name": "Right Center Midfield" },
      "jersey_number": 8
    },
    {
      "player": { "id": 4658, "name": "Keira Walsh" },
      "position": { "id": 14, "name": "Center Midfield" },
      "jersey_number": 24
    },
    {
      "player": { "id": 4645, "name": "Isobel Mary Christiansen" },
      "position": { "id": 15, "name": "Left Center Midfield" },
      "jersey_number": 11
    },
    {
      "player": { "id": 4654, "name": "Nikita Parris" },
      "position": { "id": 17, "name": "Right Wing" },
      "jersey_number": 17
    },
    {
      "player": { "id": 4635, "name": "Julia Spetsmark" },
      "position": { "id": 21, "name": "Left Wing" },
      "jersey_number": 15
    },
    {
      "player": { "id": 4650, "name": "Nadia Nadim" },
      "position": { "id": 23, "name": "Center Forward" },
      "jersey_number": 10
    }
  ]
}
</details>

<details> <summary>Types (different values)</summary>
2 / Ball Recovery: An attempt to recover a loose ball
3 / Dispossessed: Player loses ball to an opponent as a result of being tackled by a defender without attempting a dribble
4 / Duel: A 50-50 contest between two opposing players
5 / Camera On: Signals the stop of the camera to capture gameplay for a replay/video cut
6 / Block: Blocking the ball by standing in its path
8 / Offside: Offside infringement. For passes resulting in offside, see pass outcomes
9 / Clearance: Defending action to clear danger without intent to deliver to a teammate
10 / Interception: Preventing a pass from reaching its target by moving/reacting to intercept
14 / Dribble: An attempt to beat an opponent
16 / Shot: An attempt to score a goal
17 / Pressure: Applying pressure to an opposing player receiving, carrying, or releasing the ball
18 / Half Start: Referee whistle to start a match period
19 / Substitution
20 / Own Goal Against: An own goal scored against the team
21 / Foul Won: Player wins a free-kick or penalty after being fouled
22 / Foul Committed: Infringement penalised as foul play (offsides not tagged here)
23 / Goal Keeper: Goalkeeper actions
24 / Bad Behaviour: Card due to infringement outside of play
25 / Own Goal For: An own goal scored for the team
26 / Player On: A player returns to the pitch after a Player Off event
27 / Player Off: A player leaves the pitch without a substitution
28 / Shield: Player shields ball out of bounds to prevent opponent keeping it in play
30 / Pass: Ball is passed between teammates
33 / 50/50: Two players challenging to recover a loose ball
34 / Half End: Referee whistle to finish a match part
35 / Starting XI: Lists starting 11, positions, and formation
36 / Tactical Shift: Tactical change showing new positions and formation
37 / Error: On-ball mistake that leads to a shot on goal
38 / Miscontrol: Player loses ball due to bad touch
39 / Dribbled Past: Player is dribbled past by an opponent
40 / Injury Stoppage: Play stopped due to an injury
41 / Referee Ball-Drop: Referee drops the ball to continue after injury stoppage
42 / Ball Receipt: The receipt or intended receipt of a pass
43 / Carry: Player controls the ball at feet while moving or standing still
</details>

<details> <summary>Play pattern (different values)</summary>
1 / Regular Play: Not part of any special play pattern
2 / From Corner: Passage of play following a corner
3 / From Free Kick: Passage of play following a free-kick
4 / From Throw In: Passage of play following a throw-in
5 / Other
6 / From Counter: Part of a counter attack
7 / From Goal Kick: Passage of play following a goal kick
8 / From Keeper: Passage of play following a keeper distribution
9 / From Kick Off: Passage of play following a kick off
</details>