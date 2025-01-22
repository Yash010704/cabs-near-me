# Cab Locator: Finding Nearby Cabs

This project provides a C++ implementation for identifying nearby cabs based on a given customer's latitude and longitude. The program processes a JSON file (`customers.json`) containing customer details and calculates the distance between the customer's location and the given coordinates using the Great Circle Distance Formula. Results are written to an output JSON file (`answer.json`).

---

## Features
- Reads customer data from `customers.json`.
- Calculates the distance between a fixed location and customer locations using the Great Circle Distance formula.
- Outputs customers within a 50 km radius to `answer.json`.
- Simple JSON parsing using character array manipulation.

---

## Prerequisites
- C++ Compiler (e.g., GCC, Clang)
- JSON file named `customers.json` containing customer data in the following format:

```json
[
  {
    "latitude": "12.9611159",
    "longitude": "77.6362214",
    "user_id": 1,
    "name": "John Doe"
  },
  {
    "latitude": "12.9611159",
    "longitude": "77.6462214",
    "user_id": 2,
    "name": "Jane Smith"
  }
]
```

---

## How It Works
1. **Define Fixed Coordinates**: The customer's location is hardcoded as latitude `12.9611159` and longitude `77.6362214`.
2. **Read Input**: The program reads the JSON file `customers.json` containing customer locations and details.
3. **Calculate Distance**: For each customer, the program computes the distance from the fixed coordinates using the Great Circle Distance formula:
   
   
4. **Output Results**: Customers within a 50 km radius are written to the `answer.json` file in the following format:

```json
{
  "user_id": 1,
  "name": "John Doe"
}
```

---

## How to Use

### 1. Compile the Code
Compile the code using a C++ compiler:
```bash
g++ -o cab_locator cab_locator.cpp
```

### 2. Prepare Input
Ensure the `customers.json` file is in the same directory as the executable. Populate it with customer data in the specified format.

### 3. Run the Program
Run the executable:
```bash
./cab_locator
```

### 4. Check Output
Results will be saved in `answer.json` in the same directory.

---

## Code Structure
- **`main()`**: Initializes the JSON object and starts parsing the input file.
- **`json_parser()`**: Reads and processes each line of `customers.json` to extract customer attributes.
- **`distanceEarth()`**: Calculates the Great Circle Distance between two locations.
- **`distance_calculator()`**: Checks if the computed distance is within 50 km and writes qualifying customers to `answer.json`.

---

## Example
### Input (`customers.json`):
```json
[
  {
    "latitude": "12.9611159",
    "longitude": "77.6362214",
    "user_id": 1,
    "name": "John Doe"
  },
  {
    "latitude": "13.9611159",
    "longitude": "78.6362214",
    "user_id": 2,
    "name": "Jane Smith"
  }
]
```

### Output (`answer.json`):
```json
{
  "user_id": 1,
  "name": "John Doe"
}
```

---

## Limitations
- The JSON parsing logic is simplistic and may not handle complex JSON structures.
- The fixed location (latitude and longitude) is hardcoded.
- Assumes `customers.json` is well-formed.

---

## Future Enhancements
- Replace manual JSON parsing with a library like [nlohmann/json](https://github.com/nlohmann/json).
- Allow user input for fixed location coordinates.
- Add error handling for missing or malformed input files.
- Optimize for larger datasets.

---

## License
This project is open-source and available for modification and distribution.

