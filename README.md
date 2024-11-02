import tkinter as tk
from tkinter import messagebox



# Function to calculate CAPM
def calculate_capm():
    try:
        # Retrieve user input
        rf = float(rf_entry.get()) / 100  # Convert percentage to decimal
        rm = float(rm_entry.get()) / 100  # Convert percentage to decimal
        beta_val = float(beta_entry.get())
        
        # CAPM calculation
        expected_return = rf + beta_val * (rm - rf)
        
        # Display result
        result_label.config(text=f"Expected Return: {expected_return:.2%}")
        
    except ValueError:
        messagebox.showerror("Input error", "Please enter valid numeric values")

# Clear inputs
def clear_inputs():
    rf_entry.delete(0, tk.END)
    rm_entry.delete(0, tk.END)
    beta_entry.delete(0, tk.END)
    result_label.config(text="")

# Set up the GUI
root = tk.Tk()
root.title("CAPM Calculator")
root.geometry("400x400")
root.config(bg="lightgrey")

# Title Label
title_label = tk.Label(root, text="CAPM Expected Return Calculator", font=("Arial", 16), bg="lightgrey")
title_label.pack(pady=10)

# Input Fields Frame
input_frame = tk.Frame(root, bg="lightgrey")
input_frame.pack(pady=10)
# Risk-Free Rate Input
rf_label = tk.Label(input_frame, text="Risk-Free Rate (Rf) %:", font=("Arial", 14), bg="lightgrey")
rf_label.grid(row=0, column=0, pady=5)
rf_entry = tk.Entry(input_frame, font=("Arial", 14))
rf_entry.grid(row=1, column=0, pady=5)

# Expected Market Return Input
rm_label = tk.Label(input_frame, text="Expected Market Return (Rm) %:", font=("Arial", 14), bg="lightgrey")
rm_label.grid(row=2, column=0, pady=5)
rm_entry = tk.Entry(input_frame, font=("Arial", 14))
rm_entry.grid(row=3, column=0, pady=5)

# Beta of the Stock Input
beta_label = tk.Label(input_frame, text="Beta (β):", font=("Arial", 14), bg="lightgrey")
beta_label.grid(row=4, column=0, pady=5)
beta_entry = tk.Entry(input_frame, font=("Arial", 14))

beta_entry.grid(row=5, column=0, pady=5)

# Buttons Frame
button_frame = tk.Frame(root, bg="lightgrey")
button_frame.pack(pady=20)

# Calculate CAPM Button
calculate_button = tk.Button(button_frame, text="Calculate CAPM", font=("Arial", 14), bg="green", fg="white", command=calculate_capm)
calculate_button.grid(row=0, column=0, padx=10)

# Clear Button
clear_button = tk.Button(button_frame, text="Clear", font=("Arial", 14), bg="red", fg="white", command=clear_inputs)
clear_button.grid(row=0, column=1, padx=10)

# Result Label
result_label = tk.Label(root, text="", font=("Arial", 14), bg="lightgrey")
result_label.pack(pady=10)

# Run the main loop
root.mainloop()
