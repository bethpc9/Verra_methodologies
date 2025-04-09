import pandas as pd

# Load in files
land_use_csv_path = r"C:/path/Land_Cover_Hectares.csv"
classification_csv_path = r"C:/path/Land_Cover_VM_Classification.csv"

# Load the LU hectare data
df = pd.read_csv(land_use_csv_path)

# Load the classification data
classification_df = pd.read_csv(classification_csv_path, delimiter=';')

# Create a mapping of LU classes (e.g., LU_1_Hectares) to VM bins (e.g., VM 47)
lu_to_vm_map = {}
for index, row in classification_df.iterrows():
    # Map the 'Code' column (1, 2, 3, etc.) to the corresponding LU class column (LU_1_Hectares, LU_2_Hectares, etc.)
    lu_class = f"LU_{row['Code']}_Hectares"
    
    # VM columns have 'Y' for binning
    vm_bins = [col for col in classification_df.columns[4:] if row[col] == 'Y']
    lu_to_vm_map[lu_class] = vm_bins

# Print the LU to VM map to verify the mapping
print("LU to VM mapping:")
for lu_class, vm_bins in lu_to_vm_map.items():
    print(f"{lu_class}: {vm_bins}")

# Initialize a dictionary to store the sum of hectares for each VM bin
vm_bin_hectares = {bin_code: 0 for bin_code in classification_df.columns[4:]}

# Loop through each row in the LU hectares DataFrame
for _, row in df.iterrows():
    # Get the hectares for each LU class (e.g., LU_1_Hectares, LU_2_Hectares, etc.)
    hectares = {col: row[col] for col in df.columns if col.startswith('LU_')}
    
    # Print the hectares data for debugging
    print(f"Hectares for project site {row['Project_Site']}: {hectares}")
    
    # For each LU class, add its hectares to the corresponding VM bins
    for lu_class, vm_bins in lu_to_vm_map.items():
        # Extract the hectares value for the LU class (e.g., LU_1_Hectares, LU_2_Hectares, etc.)
        hectares_value = hectares.get(lu_class, 0)
        
        # Debug output to check if hectares are being correctly assigned
        if hectares_value == 0:
            print(f"Warning: No hectares for {lu_class} at site {row['Project_Site']}")
        
        # Add hectares to the appropriate VM bins
        for vm_bin in vm_bins:
            vm_bin_hectares[vm_bin] += hectares_value

# Print the summed hectares for each VM bin
print("Summed VM bin hectares:")
for vm_bin, total_hectares in vm_bin_hectares.items():
    print(f"{vm_bin}: {total_hectares}")

# Sum up the hectares for each VM bin
summarized_data = {bin_code: vm_bin_hectares[bin_code] for bin_code in vm_bin_hectares}

# Convert summarized data into a DataFrame for easier visualization
summarized_df = pd.DataFrame(summarized_data, index=[0])

# Output the results to a CSV
output_csv_path = r"C:/path/VM_Binned_Hectares.csv"
summarized_df.to_csv(output_csv_path, index=False)
