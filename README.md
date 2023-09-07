# calculator_using_python
import tkinter as tk

# Create a function to handle button clicks
def button_click(number):
    current = entry.get()
    entry.delete(0, tk.END)
    entry.insert(0, current + str(number))

# Create a function to clear the entry field
def clear():
    entry.delete(0, tk.END)

# Create a function to perform calculations
def calculate():
    try:
        result = eval(entry.get())
        entry.delete(0, tk.END)
        entry.insert(0, str(result))
    except:
        entry.delete(0, tk.END)
        entry.insert(0, "Error")

# Create the main window
window = tk.Tk()
window.title("Calculator")

# Create an entry widget for input
entry = tk.Entry(window, width=30, borderwidth=5)
entry.grid(row=0, column=0, columnspan=4)

# Create buttons for numbers and operators
buttons = [
    ('7', 1, 0), ('8', 1, 1), ('9', 1, 2), ('/', 1, 3),
    ('4', 2, 0), ('5', 2, 1), ('6', 2, 2), ('*', 2, 3),
    ('1', 3, 0), ('2', 3, 1), ('3', 3, 2), ('-', 3, 3),
    ('0', 4, 0), ('.', 4, 1), ('=', 4, 2), ('+', 4, 3),
]

for (text, row, col) in buttons:
    button = tk.Button(window, text=text, padx=20, pady=20, command=lambda text=text: button_click(text))
    button.grid(row=row, column=col)

# Create a clear button
clear_button = tk.Button(window, text='C', padx=20, pady=20, command=clear)
clear_button.grid(row=5, column=0)

# Create a calculate button
calculate_button = tk.Button(window, text='Calculate', padx=55, pady=20, command=calculate)
calculate_button.grid(row=5, column=1, columnspan=3)

# Start the GUI main loop
window.mainloop()
