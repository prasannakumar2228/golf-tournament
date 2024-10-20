This project is a Spring Boot application built to manage player scores for a golf tournament. It allows players to submit scores for individual holes, view their scores, 
and generate a leaderboard that ranks players based on their total score relative to par. The application uses an H2 in-memory database for data persistence

APIs Developed:
1. Add Player API
•	Endpoint: POST /players/add
•	Functionality: This API allows you to add a new player to the system. You simply provide the player’s name as a request parameter, and a new player record will be created in the database.
•	Request:
o	Parameter: name (String) - The name of the player.
•	Response: The newly created Player object with its details.
•	URL : curl --location --request POST 'http://localhost:8081/players/add?name=prasanna'


2. Get All Players API
•	Endpoint: GET /players/all
•	Functionality: This API retrieves a list of all players that have been added to the tournament.
•	Response: A list of Player objects.
•	URL  :  curl --location 'http://localhost:8081/players/all'



4. Submit Score API
•	Endpoint: POST /scores/submit
•	Functionality: Players can submit their score for a specific hole. This API validates the input, checks if the hole number is valid (between 1 and 18), and stores the score in the database. If the player scores under par, a notification is triggered (For Time Being we Just Displayed in Console using SYSOUT).
•	Request:
o	Body (JSON): PlayerReq object containing:
	name (String) - Player's name.
	stroke (Integer) - Number of strokes for the hole.
	holeNumber (Integer) - The hole number (1-18).
•	Response: The submitted Score object including the player's score relative to par.


•	URL : curl --location 'http://localhost:8081/scores/submit' \
           --header 'Content-Type: application/json' \
                           --data '{
                              "name": "prasanna",
              "stroke": 1,
             "holeNumber": 1
          }'


          
4. Get Player's Scores API
•	Endpoint: GET /scores/player/{name}
•	Functionality: This API retrieves all the scores submitted by a specific player. It uses the player’s name as a path variable and returns the list of scores for that player.
•	Request:
o	Path Variable: name (String) - The name of the player.
•	Response: A list of Score objects showing the player’s score for each hole.
•	URI : curl --location 'http://localhost:8081/scores/player/prasanna'




5. Get Leaderboard API
•	Endpoint: GET /scores/leaderboard
•	Functionality: This API generates a leaderboard showing players ranked by their total score relative to par. It returns each player's name, total score relative to par, and the number of holes completed.
•	Response: A list of LeaderboardResponseDTO objects .
•	URI  :  curl --location 'http://localhost:8081/scores/leaderboard'

