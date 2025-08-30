import os

# Initialize the to-do list
tasks = []

# Display the menu
def display_menu():
    print("\nTo-Do List App")
    print("1. View Tasks")
    print("2. Add Task")
    print("3. Edit Task")
    print("4. Delete Task")
    print("5. Exit")

# View tasks
def view_tasks():
    if tasks:
        print("\nYour Tasks:")
        for index, task in enumerate(tasks, 1):
            print(f"{index}. {task}")
    else:
        print("\nNo tasks to show.")

# Add a task
def add_task():
    task = input("\nEnter the new task: ")
    tasks.append(task)
    print(f"Task '{task}' added.")

# Edit a task
def edit_task():
    view_tasks()
    try:
        task_number = int(input("\nEnter the number of the task to edit: "))
        if 1 <= task_number <= len(tasks):
            new_task = input("Enter the updated task: ")
            tasks[task_number - 1] = new_task
            print(f"Task {task_number} updated.")
        else:
            print("Invalid task number.")
    except ValueError:
        print("Invalid input. Please enter a number.")

# Delete a task
def delete_task():
    view_tasks()
    try:
        task_number = int(input("\nEnter the number of the task to delete: "))
        if 1 <= task_number <= len(tasks):
            deleted_task = tasks.pop(task_number - 1)
            print(f"Task '{deleted_task}' deleted.")
        else:
            print("Invalid task number.")
    except ValueError:
        print("Invalid input. Please enter a number.")

# Main function
def main():
    while True:
        display_menu()
        choice = input("\nEnter your choice: ")

        if choice == '1':
            view_tasks()
        elif choice == '2':
            add_task()
        elif choice == '3':
            edit_task()
        elif choice == '4':
            delete_task()
        elif choice == '5':
            print("Exiting the app.")
            break
        else:
            print("Invalid choice. Please select a valid option.")

if __name__ == "__main__":
    main()
