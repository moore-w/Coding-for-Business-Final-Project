# Coding for Business - Final Project
Using data from an MLB data set, I created an interactive platform that allows users to explore team and player statistics. 


Users can:
- Select any MLB team from a dropdown menu of all 30 teams to view the team logo and roster
- Choose a player from the roster and a year to view their statistics from the selected season

# Example Code Snippet

```python
import requests
import ipywidgets as widgets
from IPython.display import display, HTML

# API setup
API_base = "https://statsapi.mlb.com/api/v1"
Teams_URL = f"{API_base}/teams?sportId=1"

sess = requests.Session()
sess.headers.update({ "User-Agent": "mlb-jupyter-dashboard/1.0" })

# Retrieve teams
r = sess.get(Teams_URL, timeout=10)
team_list = r.json().get("teams", [])

# Create a simple dropdown for team selection
team_dropdown = widgets.Dropdown(
    options=[(t.get("name", ""), t.get("id")) for t in team_list],
    description="Team:"
)
display(team_dropdown)
