import tkinter as tk
from tkinter import messagebox

# Function to calculate the total balances and deference
def calculate_totals():
    try:
        # Get values from the input fields and convert them to float
        cash_open = float(entry_cash_open.get())
        cash_close = float(entry_cash_close.get())
        dialog_open = float(entry_dialog_open.get())
        dialog_close = float(entry_dialog_close.get())
        mobitel_open = float(entry_mobitel_open.get())
        mobitel_close = float(entry_mobitel_close.get())
        airtel_open = float(entry_airtel_open.get())
        airtel_close = float(entry_airtel_close.get())
        hutch_open = float(entry_hutch_open.get())
        hutch_close = float(entry_hutch_close.get())
        boc_open = float(entry_boc_open.get())
        boc_close = float(entry_boc_close.get())
        hnb_open = float(entry_hnb_open.get())
        hnb_close = float(entry_hnb_close.get())
        ez_open = float(entry_ez_open.get())
        ez_close = float(entry_ez_close.get())
        
        # Calculate the totals for Open and Close balances
        total_open = (cash_open + dialog_open + mobitel_open + airtel_open +
                      hutch_open + boc_open + hnb_open + ez_open)
        total_close = (cash_close + dialog_close + mobitel_close + airtel_close +
                       hutch_close + boc_close + hnb_close + ez_close)
        
        # Calculate the deference
        deference = total_open - total_close

        # Update the labels to show the results
        label_total_open.config(text=f"Total Open Balance: {total_open:.2f}")
        label_total_close.config(text=f"Total Close Balance: {total_close:.2f}")
        label_deference.config(text=f"Deference: {deference:.2f}")
        
    except ValueError:
        messagebox.showerror("Input Error", "Please enter valid numbers.")

# Initialize the main window
root = tk.Tk()
root.title("Balance Tracker")

# Labels and entry fields for each item
labels = ["Cash", "Dialog", "Mobitel", "Airtel", "Hutch", "BOC", "HNB", "Ez"]
entries_open = []
entries_close = []

for i, label in enumerate(labels):
    tk.Label(root, text=label).grid(row=i, column=0, padx=10, pady=5)
    entry_open = tk.Entry(root)
    entry_open.grid(row=i, column=1, padx=10, pady=5)
    entry_close = tk.Entry(root)
    entry_close.grid(row=i, column=2, padx=10, pady=5)
    entries_open.append(entry_open)
    entries_close.append(entry_close)

# Assign entry variables
(entry_cash_open, entry_dialog_open, entry_mobitel_open, entry_airtel_open,
 entry_hutch_open, entry_boc_open, entry_hnb_open, entry_ez_open) = entries_open

(entry_cash_close, entry_dialog_close, entry_mobitel_close, entry_airtel_close,
 entry_hutch_close, entry_boc_close, entry_hnb_close, entry_ez_close) = entries_close

# Button to calculate totals
calculate_button = tk.Button(root, text="Calculate Totals", command=calculate_totals)
calculate_button.grid(row=len(labels), column=0, columnspan=3, pady=10)

# Labels to display results
label_total_open = tk.Label(root, text="Total Open Balance: 0.00")
label_total_open.grid(row=len(labels)+1, column=0, columnspan=3, pady=5)

label_total_close = tk.Label(root, text="Total Close Balance: 0.00")
label_total_close.grid(row=len(labels)+2, column=0, columnspan=3, pady=5)

label_deference = tk.Label(root, text="Deference: 0.00")
label_deference.grid(row=len(labels)+3, column=0, columnspan=3, pady=5)

# Start the Tkinter event loop
root.mainloop()
