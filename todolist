import tkinter as tk
from tkinter import messagebox

class TodoApp:
    def __init__(self, root):
        self.root = root
        self.root.title("To-Do List Application")
        self.root.geometry("400x550")
        self.tasks = []
        self.title_label = tk.Label(root, text="My To-Do List", font=("Arial", 18, "bold"))
        self.title_label.pack(pady=10)
        self.task_entry = tk.Entry(root, width=40)
        self.task_entry.pack(pady=10)
        self.add_button = tk.Button(root, text="Add Task", width=15, command=self.add_task)
        self.add_button.pack(pady=5)
        self.update_button = tk.Button(root, text="Update Task", width=15, command=self.update_task)
        self.update_button.pack(pady=5)
        self.delete_button = tk.Button(root, text="Delete Task", width=15, command=self.delete_task)
        self.delete_button.pack(pady=5)
        self.complete_button = tk.Button(root, text="Mark Completed", width=15, command=self.complete_task)
        self.complete_button.pack(pady=5)
        self.listbox = tk.Listbox(root, width=50, height=15, selectmode=tk.SINGLE)
        self.listbox.pack(pady=10)
    def add_task(self):
        task = self.task_entry.get()
        if task != "":
            self.tasks.append(task)
            self.update_listbox()
            self.task_entry.delete(0, tk.END)
        else:
            messagebox.showwarning("Warning", "You must enter a task!")
    def delete_task(self):
        try:
            selected_index = self.listbox.curselection()[0]
            del self.tasks[selected_index]
            self.update_listbox()
        except IndexError:
            messagebox.showwarning("Warning", "You must select a task to delete!")
    def complete_task(self):
        try:
            selected_index = self.listbox.curselection()[0]
            self.tasks[selected_index] = self.tasks[selected_index] + " ✔"
            self.update_listbox()
        except IndexError:
            messagebox.showwarning("Warning", "You must select a task to mark complete!")
    def update_task(self):
        try:
            selected_index = self.listbox.curselection()[0]
            new_task = self.task_entry.get()
            if new_task != "":
                self.tasks[selected_index] = new_task
                self.update_listbox()
                self.task_entry.delete(0, tk.END)
            else:
                messagebox.showwarning("Warning", "You must enter a new task to update!")
        except IndexError:
            messagebox.showwarning("Warning", "You must select a task to update!")
    def update_listbox(self):
        self.listbox.delete(0, tk.END)
        for task in self.tasks:
            self.listbox.insert(tk.END, task)
if __name__ == "__main__":
    root = tk.Tk()
    app = TodoApp(root)
    root.mainloop()
