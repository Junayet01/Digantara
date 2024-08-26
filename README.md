# Satellite Position Calculation and Filtering

This project calculates satellite positions using TLE data and filters them based on a user-defined geographical rectangle. The calculations are accelerated using CuPy for GPU processing.

## Prerequisites

- Python 3.x
- cupy
- pyproj
- sgp4

## Installation

1. Clone the repository:

```shell
git clone https://github.com/Junayet01/Digantara.git

```
2. Create a virtual environment and activate it:
```shell
python -m venv venv
.\venv\Scripts\activate  # On Windows
# source venv/bin/activate  # On macOS/Linux
```



3. Install the required dependencies:
   ```shell
   pip install -r requirements.txt
   ```
   
## Usage
1.Prepare the TLE data by creating a text file ('30sats.txt') with the TLE data for the satellites you want to track.

2.Run the script:
  ```shell
python main.py
```
3.Enter the start date in the format 'YYYY-MM-DD' when prompted.

4.Enter the latitude and longitude for the four corners of the rectangle when prompted.

5.The script will calculate the positions of the satellites and filter them based on the user-defined rectangle. The filtered positions will be displayed on the console.

## Functions

### `read_tle(file_path)`
Reads TLE data from a file and creates satellite objects.

### `calculate_positions(satellites, start_date, minutes_interval=1)`
Calculates satellite positions using CuPy for acceleration.

### `get_start_date()`
Prompts the user to enter a start date.

### `ecef2lla(positions)`
Converts ECEF coordinates to LLA coordinates using CuPy.

### `get_user_rectangle()`
Prompts the user to enter the coordinates of a rectangle.

### `get_rectangle_bounds(coords)`
Calculates the bounds of the rectangle from the given coordinates.

### `filter_positions_by_rectangle(longs, lats, bounds)`
Filters positions based on the user-defined rectangle using CuPy.
