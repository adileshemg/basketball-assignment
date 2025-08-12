# Basketball statistics assignment

We want to learn more about basketball statistics.
Your job is to write a small data pipeline that analyses a json file of basketball games and 
answers a specific question based on the data.


The `games.json` has a list of game entries of this form:
```json
{
    "date": "2018-01-21T00:00:00.000Z",
    "home_team": {
        "abbreviation": "BOS",
        "city": "Boston",
        "conference": "East",
        "division": "Atlantic",
        "full_name": "Boston Celtics",
        "id": 2,
        "name": "Celtics"
    },
    "visitor_team": {
        "abbreviation": "ORL",
        "city": "Orlando",
        "conference": "East",
        "division": "Southeast",
        "full_name": "Orlando Magic",
        "id": 22,
        "name": "Magic"
    },
    "home_team_score": 95,
    "visitor_team_score": 103,
    "id": 35060,
    "period": 4,
    "postseason": false,
    "season": 2017,
    "status": "Final",
    "time": " "
}
```


## Your task
**Hypothesis:** basketball teams tend to win more often when they are the home team.

You have been assigned to give us your informed opinion on the hypothesis correctness, based on data extracted from the raw json file.

#### In order to do that, you will create a small data pipeline consisting of 3 steps, all using the filesystem for simple data transfers.

**Set the year to work on as a static variable and use 2020**

### Step 1: Identify new files in a directory (on local disk)
- In the `team-name/` directory, new files are created with the "full_name" of a team as the filename
- Implement an 'always on' process that will trigger the next step when a new file arrives with the "full_name"

### Step 2: Create a raw data file using team name
- **Input:** "full_name" of a team
- Extract only the data you need to test the hypothesis for the given team from the `games.json` raw data file
- **Output:** a data file with the "full_name" of a team as its filename in the `team-results/` directory

### Step 3: Test the hypothesis per team data file
- **Input:** step 2's output
- Calculate whether the hypothesis was true for this team
- **Output:** a True/False text file with the "full_name" of a team as its filename in the `team-hypothesis-results/` directory

### Step 4: Test the hypothesis for all teams currently processed
- **Input:** step 3's outputs
- Summarize the hypothesis correctness for all teams already processed
- **Output:** a file called `totals.json` in the `total-hypothesis-results/` directory
- format `{ hypothesis_true_count: int, total_teams_count: int }`

### First focus on getting a _working_ solution.

- Make the code as production-worthy as possible (e.g. DRY, readable, etc).
- Consider good coding design and practices along the way (e.g. OOP, SOLID)
