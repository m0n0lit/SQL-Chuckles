import tkinter as tk
import sqlite3

def sql_injection_gui():
    """
    This function creates a GUI that allows users to perform SQL injections.
    """
    # Create the main window
    window = tk.Tk()
    window.title("SQL Injection Tool")
    window.geometry("400x200")

    # Create the label for the database name
    db_name_label = tk.Label(window, text="Database Name:")
    db_name_label.grid(column=0, row=0)

    # Create the entry field for the database name
    db_name_entry = tk.Entry(window, width=20)
    db_name_entry.grid(column=1, row=0)

    # Create the label for the SQL query
    sql_query_label = tk.Label(window, text="SQL Query:")
    sql_query_label.grid(column=0, row=1)

    # Create the entry field for the SQL query
    sql_query_entry = tk.Entry(window, width=20)
    sql_query_entry.grid(column=1, row=1)

    # Create the button to execute the SQL query
    execute_btn = tk.Button(window, text="Execute", command=execute_query)
    execute_btn.grid(column=1, row=2)

    # Create the label for the result
    result_label = tk.Label(window, text="Result:")
    result_label.grid(column=0, row=3)

    # Create the text field for the result
    result_text = tk.Text(window, height=5, width=30)
    result_text.grid(column=1, row=3)

    # Create the button to clear the result
    clear_btn = tk.Button(window, text="Clear", command=clear_result)
    clear_btn.grid(column=1, row=4)

    window.mainloop()

def execute_query():
    """
    This function executes the SQL query entered by the user.
    """
    # Get the database name and SQL query from the entry fields
    db_name = db_name_entry.get()
    sql_query = sql_query_entry.get()

    # Connect to the database
    try:
        conn = sqlite3.connect(db_name)
        cursor = conn.cursor()
    except Exception as e:
        print("Error connecting to database: {}".format(e))
        return

    # Execute the SQL query
    try:
        cursor.execute(sql_query)
        result = cursor.fetchall()
    except Exception as e:
        print("Error executing query: {}".format(e))
        return

    # Display the result in the text field
    result_text.delete('1.0', tk.END)
    for row in result:
        result_text.insert(tk.END, row)

def clear_result():
    """
    This function clears the result text field.
    """
    result_text.delete('1.0', tk.END)

if __name__ == "__main__":
    sql_injection_gui()
