# Calculator-app-using-python
import tkinter as tk

def button_click(number):
    current = entry.get()
    entry.delete(0, tk.END)
    entry.insert(0, current + str(number))

def button_clear():
    entry.delete(0, tk.END)

def button_add():
    global first_num
    global operation
    operation = "add"
    first_num = float(entry.get())
    entry.delete(0, tk.END)

def button_subtract():
    global first_num
    global operation
    operation = "subtract"
    first_num = float(entry.get())
    entry.delete(0, tk.END)

def button_multiply():
    global first_num
    global operation
    operation = "multiply"
    first_num = float(entry.get())
    entry.delete(0, tk.END)

def button_divide():
    global first_num
    global operation
    operation = "divide"
    first_num = float(entry.get())
    entry.delete(0, tk.END)

def button_equal():
    second_num = float(entry.get())
    entry.delete(0, tk.END)

    if operation == "add":
        entry.insert(0, first_num + second_num)
    elif operation == "subtract":
        entry.insert(0, first_num - second_num)
    elif operation == "multiply":
        entry.insert(0, first_num * second_num)
    elif operation == "divide":
        entry.insert(0, first_num / second_num)

# UI Setup
root = tk.Tk()
root.title("Calculator")

entry = tk.Entry(root, width=30, borderwidth=5, font=("Arial", 16))
entry.grid(row=0, column=0, columnspan=4, pady=10)

# Buttons
buttons = [
    ('7', 1, 0), ('8', 1, 1), ('9', 1, 2),
    ('4', 2, 0), ('5', 2, 1), ('6', 2, 2),
    ('1', 3, 0), ('2', 3, 1), ('3', 3, 2),
    ('0', 4, 1)
]

for (text, row, col) in buttons:
    tk.Button(root, text=text, width=5, height=2, font=("Arial", 14),
              command=lambda t=text: button_click(t)).grid(row=row, column=col)

tk.Button(root, text='+', width=5, height=2, font=("Arial", 14),
          command=button_add).grid(row=1, column=3)

tk.Button(root, text='-', width=5, height=2, font=("Arial", 14),
          command=button_subtract).grid(row=2, column=3)

tk.Button(root, text='×', width=5, height=2, font=("Arial", 14),
          command=button_multiply).grid(row=3, column=3)

tk.Button(root, text='÷', width=5, height=2, font=("Arial", 14),
          command=button_divide).grid(row=4, column=3)

tk.Button(root, text='C', width=5, height=2, font=("Arial", 14),
          command=button_clear).grid(row=4, column=0)

tk.Button(root, text='=', width=5, height=2, font=("Arial", 14),
          command=button_equal).grid(row=4, column=2)

root.mainloop()
