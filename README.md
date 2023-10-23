# Data-Structure-Project
package K22ug;

import java.util.ArrayList;
import java.util.Scanner;

class Task {
    String description;
    String deadline;
    String priority;
    boolean completed;

    public Task(String description, String deadline, String priority) {
        this.description = description;
        this.deadline = deadline;
        this.priority = priority;
        this.completed = false;
    }
}

class TaskScheduler {
    ArrayList<Task> tasks;

    public TaskScheduler() {
        this.tasks = new ArrayList<>();
    }

    // Method to add a new task to the task list
    public void addTask(String description, String deadline, String priority) {
        tasks.add(new Task(description, deadline, priority));
    }

    // Method to modify an existing task based on task ID
    public void modifyTask(int taskId, String newDescription, String newDeadline, String newPriority) {
        // Check if the task ID is valid
        if (taskId >= 1 && taskId <= tasks.size()) {
            Task task = tasks.get(taskId - 1);
            // Update task details
            task.description = newDescription;
            task.deadline = newDeadline;
            task.priority = newPriority;
            System.out.println("Task modified successfully.");
        } else {
            System.out.println("Invalid task number.");
        }
    }

    // Method to remove an existing task based on task ID
    public void removeTask(int taskId) {
        // Check if the task ID is valid
        if (taskId >= 1 && taskId <= tasks.size()) {
            tasks.remove(taskId - 1);
            System.out.println("Task removed successfully.");
        } else {
            System.out.println("Invalid task number.");
        }
    }

    // Method to view all tasks in the task list
    public void viewTasks() {
        System.out.println("Tasks:");
        for (int i = 0; i < tasks.size(); i++) {
            Task task = tasks.get(i);
            System.out.println((i + 1) + ". Description: " + task.description);
            System.out.println("   Deadline: " + task.deadline);
            System.out.println("   Priority: " + task.priority);
            System.out.println("   Completed: " + (task.completed ? "Yes" : "No"));
            System.out.println("------------");
        }
    }

    // Method to mark a task as completed based on task ID
    public void markAsCompleted(int taskId) {
        // Check if the task ID is valid
        if (taskId >= 1 && taskId <= tasks.size()) {
            Task task = tasks.get(taskId - 1);
            task.completed = true;
            System.out.println("Task marked as completed.");
        } else {
            System.out.println("Invalid task number.");
        }
    }
}

public class Project {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        TaskScheduler scheduler = new TaskScheduler();

        boolean isRunning = true;
        while (isRunning) {
            // Display menu options to the user
            System.out.println("Options:");
            System.out.println("1. Add Task");
            System.out.println("2. Modify Task");
            System.out.println("3. Remove Task");
            System.out.println("4. View Tasks");
            System.out.println("5. Mark Task as Completed");
            System.out.println("6. Exit");
            System.out.print("Enter your choice: ");

            int choice = scanner.nextInt();
            scanner.nextLine();  // Consume the newline character

            // Switch statement to handle user choices
            switch (choice) {
                case 1:
                    // Task addition functionality
                    System.out.println("Enter task description:");
                    String description = scanner.nextLine();
                    System.out.println("Enter task deadline (YYYY-MM-DD):");
                    String deadline = scanner.nextLine();
                    System.out.println("Enter task priority (High, Medium, Low):");
                    String priority = scanner.nextLine();
                    scheduler.addTask(description, deadline, priority);
                    System.out.println("Task added successfully!");
                    break;
                case 2:
                    // Task modification functionality
                    System.out.println("Enter the task number to modify:");
                    int taskIdModify = scanner.nextInt();
                    scanner.nextLine();  // Consume the newline character
                    System.out.println("Enter new task description:");
                    String newDescription = scanner.nextLine();
                    System.out.println("Enter new task deadline (YYYY-MM-DD):");
                    String newDeadline = scanner.nextLine();
                    System.out.println("Enter new task priority (High, Medium, Low):");
                    String newPriority = scanner.nextLine();
                    scheduler.modifyTask(taskIdModify, newDescription, newDeadline, newPriority);
                    break;
                case 3:
                    // Task removal functionality
                    System.out.println("Enter the task number to remove:");
                    int taskIdRemove = scanner.nextInt();
                    scanner.nextLine();  // Consume the newline character
                    scheduler.removeTask(taskIdRemove);
                    break;
                case 4:
                    // View tasks functionality
                    scheduler.viewTasks();
                    break;
                case 5:
                    // Mark task as completed functionality
                    System.out.println("Enter the task number to mark as completed:");
                    int taskIdComplete = scanner.nextInt();
                    scanner.nextLine();  // Consume the newline character
                    scheduler.markAsCompleted(taskIdComplete);
                    break;
                case 6:
                    // Exit the program
                    isRunning = false;
                    System.out.println("Exiting the task scheduler. Goodbye!");
                    break;
                default:
                    // Handle invalid choices
                    System.out.println("Invalid choice. Please try again.");
            }
        }

        // Close the scanner
        scanner.close();
    }
}
