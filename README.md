# To-do-Application
# todo.py

# List to store all To-Do items
todo_list = []

# Function to add a new To-Do item
def add_todo():
    title = input("Enter the title of the To-Do: ")
    date = input("Enter the date (YYYY-MM-DD): ")
    todo = {"title": title, "date": date}
    todo_list.append(todo)
    print("✅ To-Do added successfully.\n")

# Function to display all To-Do items
def view_todos():
    if not todo_list:
        print("📭 No To-Dos to show.\n")
        return
    print("📝 Your To-Do List:")
    for idx, todo in enumerate(todo_list, start=1):
        print(f"{idx}. {todo['title']} (Date: {todo['date']})")
    print()

# Function to delete a specific To-Do item
def delete_todo():
    view_todos()
    if not todo_list:
        return
    try:
        index = int(input("Enter the number of the To-Do to delete: ")) - 1
        if 0 <= index < len(todo_list):
            removed = todo_list.pop(index)
            print(f"🗑️ Deleted: {removed['title']}\n")
        else:
            print("❌ Invalid number. Please try again.\n")
    except ValueError:
        print("❌ Please enter a valid number.\n")

# Function to delete all To-Do items
def delete_all_todos():
    confirm = input("Are you sure you want to delete all To-Dos? (y/n): ")
    if confirm.lower() == 'y':
        todo_list.clear()
        print("🧹 All To-Dos deleted.\n")
    else:
        print("Cancelled.\n")

# Main menu function
def menu():
    while True:
        print("===== 📋 To-Do List Menu =====")
        print("1. Add To-Do")
        print("2. View To-Dos")
        print("3. Delete a To-Do")
        print("4. Delete All To-Dos")
        print("5. Exit")
        choice = input("Enter your choice (1-5): ")

        if choice == '1':
            add_todo()
        elif choice == '2':
            view_todos()
        elif choice == '3':
            delete_todo()
        elif choice == '4':
            delete_all_todos()
        elif choice == '5':
            print("👋 Exiting... Have a productive day!")
            break
        else:
            print("❌ Invalid choice. Please try again.\n")

# Start the program
if __name__ == "__main__":
    menu()
