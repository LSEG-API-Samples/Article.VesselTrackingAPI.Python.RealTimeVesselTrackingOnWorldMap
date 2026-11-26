# [Real-Time Vessel Tracking with Python and WebSocket Streaming](https://developers.lseg.com/en/article-catalog/article/vessel-tracking-part-2-vessel-tracking-websocket-streaming)

This project connects to the Vessel Tracking API's WebSocket interface, subscribes to a vessel, and shows its live positions and the path it has followed on a world map and a close-up map.

It is Part 2 of a two-part series. Part 1, [Visualizing Historical Vessel Positions on a World Map with the Vessel Tracking API and Python](https://developers.lseg.com/en/article-catalog/article/vessel-tracking-part-1-visualizing-historical-vessel-positions), replays recent position history from the REST API.

## Prerequisites

- Python 3.10 or later
- Visual Studio Code with the Jupyter extension (or JupyterLab)
- A Vessel Tracking API key that is entitled to the vessel you want to watch
- Internet access for the OpenStreetMap tiles used by the maps

## Installation

Install the required packages:

```powershell
py -m pip install --upgrade pip
py -m pip install -r requirements.txt
```

## API configuration

Create a `config.ini` file in the same directory as the notebook:

```ini
[vessel_tracking]
api_key = apikey-v1 YOUR_API_KEY
```

Do not commit this file. Add it to `.gitignore`:

```gitignore
config.ini
.venv/
.ipynb_checkpoints/
```

## Run the notebook

Open `real-time-vessel-tracking-websocket.ipynb`, set `IMO` in step 2 to a vessel you are entitled to see, and run the cells one at a time, in order, up to step 7.

The notebook will:

1. Read the vessel's latest position from the REST API.
2. Request a single-use ticket and connect to the WebSocket service.
3. Subscribe to the vessel and keep the connection alive.
4. Draw each position update on a world map and a close-up map.

Notes:

- Do not use **Run All**. Steps 8 and 9 stop tracking and clear the maps, so they run straight after step 7 starts it.
- Positions arrive only when the vessel reports them, so the first update can take a couple of minutes. The status line above the maps shows how many positions have arrived and when the last message was received.
- Run step 8 to stop tracking and step 9 to clear the maps.
- Before sharing the notebook, clear its outputs because they can contain licensed vessel data.

<img width="1263" height="950" alt="vessel-stream-img-1" src="https://github.com/user-attachments/assets/2ef6704b-7b8c-4d86-97dc-6110e87dc090" />
