# Satellite Position Calculation and Filtering

## Main.py

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



## Main2.py

# Satellite Position Calculation and Filtering

This project calculates the positions of satellites based on TLE (Two-Line Element) data and filters the positions within a user-defined rectangular area. The calculations are optimized using CuPy for GPU acceleration.

## Prerequisites

- Python 3.7+
- CuPy
- PyProj
- SGP4
- Aiofiles

## Installation

1. **Clone the repository**:
    ```sh
    git clone https://github.com/Junayet01/Digantara.git
    cd Main2.py
    ```

2. **Create a virtual environment** (optional but recommended):
    ```sh
    python -m venv venv
    source venv/bin/activate  # On Windows use `venv\Scripts\activate`
    ```

3. **Install the required packages**:
    ```sh
    pip install cupy pyproj sgp4 aiofiles
    ```

## Usage

1. **Prepare the TLE data file**:
    - Ensure you have a TLE data file named `30000sats.txt` in the project directory. This file should contain TLE data for the satellites.

2. **Run the script**:
    ```sh
    python Main2.py
    ```

3. **Follow the prompts**:
    - Enter the start date in `YYYY-MM-DD` format.
    - Enter the latitude and longitude for the four corners of the rectangle.

## Code Overview

### Asynchronous TLE Reading

The `read_tle_async` function reads TLE data asynchronously using `aiofiles` and `asyncio`.

```python
async def read_tle_async(file_path):
    satellites = []
    async with aiofiles.open(file_path, 'r') as file:
        while True:
            line1 = await file.readline()
            line2 = await file.readline()
            if not line2:
                break
            sat = Satrec.twoline2rv(line1.strip(), line2.strip())
            satellites.append(sat)
    return satellites
```
### Satellite Position Calculation
The calculate_positions function processes satellite positions in batches to better utilize GPU resources.
```python
 def calculate_positions(satellites, start_date, minutes_interval=1, batch_size=10):
# Function implementation
   ```
Function implementation
### ECEF to LLA Conversion
The ecef2lla function converts positions from ECEF to LLA coordinates using PyProj.
```python
 def ecef2lla(positions):
    # Function implementation
   ```

### Filtering Positions
The filter_positions_by_rectangle function filters positions within the user-defined rectangle.
```python
def filter_positions_by_rectangle(longs, lats, bounds):
    
    # Function implementation
   ```
### Example
```python
Enter the start date in YYYY-MM-DD format: 2023-10-01
Please enter the latitude and longitude for the four corners of the rectangle:
Enter latitude for corner 1: 10.0
Enter longitude for corner 1: 20.0
Enter latitude for corner 2: 10.0
Enter longitude for corner 2: 30.0
Enter latitude for corner 3: 20.0
Enter longitude for corner 3: 30.0
Enter latitude for corner 4: 20.0
Enter longitude for corner 4: 20.0
   ```

