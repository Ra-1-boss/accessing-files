# accessing-files
# Example of working with smart meter data files

def process_engineering_data(filename):
    # 1. Create a new file for writing (overwrites if exists)
    with open(filename, 'w') as f:
        # Write header
        f.write("timestamp,voltage,current,power,frequency\n")
        
        # Write some sample data
        f.write("2025-04-29 21:00:00,230.1,5.32,1223.1,49.98\n")
        f.write("2025-04-29 21:15:00,229.8,5.45,1252.4,49.97\n")
    
    # 2. Open existing file for reading
    with open(filename, 'r') as f:
        # Read entire file contents
        content = f.read()
        print("Full file content:")
        print(content)
        
        # Reset file pointer to beginning
        f.seek(0)
        
        # Read one line at a time
        print("\nReading line by line:")
        line1 = f.readline()
        line2 = f.readline()
        print("Header:", line1.strip())
        print("First reading:", line2.strip())
        
        # Reset file pointer to beginning
        f.seek(0)
        
        # Read all lines into a list
        lines = f.readlines()
        print("\nAll lines as list:")
        for line in lines:
            print(line.strip())
    
    # 3. Open file for appending to add more data
    with open(filename, 'a') as f:
        # Append new readings
        f.write("2025-04-29 21:30:00,230.0,5.28,1214.4,49.99\n")
        f.write("2025-04-29 21:45:00,229.9,5.37,1234.5,50.01\n")
        
        # Alternatively, write multiple lines at once
        new_readings = [
            "2025-04-29 22:00:00,229.7,5.41,1241.7,50.00\n",
            "2025-04-29 22:15:00,230.2,5.35,1231.9,49.99\n"
        ]
        f.writelines(new_readings)

# Run the function
process_engineering_data("smart_meter_readings.csv")
