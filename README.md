# Coding for Business - Final Project
Using data from an MLB data set, I created an interactive platform that allows users to explore team and player statistics. 


Users can:
- Search for any MLB team to view the team logo
- Select a team from a dropdown menu of all 30 MLB teams
- View the team roster with player positions
- Choose a player from the roster and a year to view their statistics from that season

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
```


For the full interactive notebook, see: https://github.com/moore-w/Coding-for-Business-Final-Project/blob/main/Will%20Moore%20-%20Final%20Project.ipynb


<img width="592" height="301" alt="Screenshot 2026-01-20 at 5 57 14 PM" src="https://github.com/user-attachments/assets/90c46b45-d0a9-4719-8bbe-396783a49373" />

