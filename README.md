# SQL-IPL-Match-Scorecard-Database-Design-and-Implementation
This project designs a relational database for IPL match details, focusing on RCB vs. CSK. It includes tables for venues, teams, players, matches, innings, and ball-by-ball scores. The goal is to generate match summaries and scorecards for display on a website, ensuring comprehensive data storage and retrieval.
Project Overview
This project focuses on designing and implementing a relational database for storing and querying information about IPL (Indian Premier League) matches. The database includes detailed data for a specific match between the Royal Challengers Bangalore (RCB) and the Chennai Super Kings (CSK). The aim is to create a comprehensive structure to store match details, including venue, teams, players, innings, and ball-by-ball scores, and to facilitate the generation of match summaries and scorecards for display on a website.

Database Design
Tables
Venue

venue_id (INTEGER, Primary Key)
venue_name (VARCHAR(200), Unique, Not Null)
Team

team_id (INTEGER, Primary Key)
team_name (VARCHAR(100), Unique, Not Null)
Player

player_id (INTEGER, Primary Key)
player_name (VARCHAR(100), Not Null)
team_id (INTEGER, Foreign Key references team_id in Team table, Not Null)
Match

match_id (INTEGER, Primary Key)
match_date (VARCHAR(10), Not Null)
venue_id (INTEGER, Foreign Key references venue_id in Venue table, Not Null)
Innings

match_id (INTEGER, Foreign Key references match_id in Match table, Not Null)
innings_no (INTEGER, Not Null)
batting_team_id (INTEGER, Foreign Key references team_id in Team table, Not Null)
bowling_team_id (INTEGER, Foreign Key references team_id in Team table, Not Null)
Primary Key: (match_id, innings_no)
Score_by_ball

match_id (INTEGER, Foreign Key references match_id in Match table, Not Null)
innings_no (INTEGER, Foreign Key references innings_no in Innings table, Not Null)
ball_no (FLOAT, Not Null)
striker_id (INTEGER, Foreign Key references player_id in Player table, Not Null)
non_striker_id (INTEGER, Foreign Key references player_id in Player table, Not Null)
bowler_id (INTEGER, Foreign Key references player_id in Player table, Not Null)
runs_off_bat (INTEGER, Not Null)
extras (INTEGER, Not Null)
wides (INTEGER, Not Null)
noballs (INTEGER, Not Null)
byes (INTEGER, Not Null)
legbyes (INTEGER, Not Null)
penalty (INTEGER, Not Null)
wicket_type (VARCHAR(200), Not Null)
dismissed_player_id (INTEGER, Foreign Key references player_id in Player table)
Primary Key: (match_id, innings_no, ball_no)
Result

match_id (INTEGER, Foreign Key references match_id in Match table, Not Null)
winning_team_id (INTEGER, Foreign Key references team_id in Team table, Not Null)
margin (INTEGER, Not Null)
Primary Key: (match_id)
