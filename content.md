# Ruby Gym: Todo List

In this exercise, you will create a class called `TodoList` that represents a simple to-do list. This class will allow users to add tasks, remove tasks, and display all tasks.

This is practice for everything in [Bridge to Rails: Defining and using Classes](/lessons/573-classes-in-ruby): a class with an `initialize` method, an instance variable, and instance methods that use it.

## Objectives

### 1. Create the `TodoList` Class:
- In `initialize`, set an instance variable `@tasks` to an empty array.

### 2. Add a `add_task` Method:
- Define a method `add_task` that takes a single argument, `task`.
- This method should add the given task (a string) to the `@tasks` array.

### 3. Add a `remove_task` Method:
- Define a method `remove_task` that takes a single argument, `task`.
- This method should remove the given task from the `@tasks` array.
- If the task is not found in the list, print `"Task not found"`.

### 4. Add a `display_tasks` Method:
- Define a method `display_tasks` that prints all tasks in the `@tasks` array, each on its own line.
- If no tasks are available, print `"No tasks in the list"`.

## Tips
- Implement the `TodoList` class and its methods as described.
- Try running in your own codespace
- Add lots of `puts` statements to debug

## Exercise

**Note:** The tests below are expecting you to use `puts` rather than `pp` when you print out strings. So be sure to use `puts` in your code when printing those strings.

```ruby
# write your program below

todo_list = TodoList.new
todo_list.add_task("Buy groceries")
todo_list.add_task("Walk the dog")
todo_list.display_tasks
# Expected Output:
# Buy groceries
# Walk the dog

todo_list.remove_task("Walk the dog")
todo_list.display_tasks
# Expected Output:
# Buy groceries

todo_list.remove_task("Go to the gym")
# Expected Output:
# Task not found
```
{: .codeblock #todo_list title="Todo List" points="1"}

```ruby
describe "TodoList" do
  it "initializes with an empty tasks list" do
    todo_list = TodoList.new
    expect(todo_list.instance_variable_get(:@tasks)).to eq([])
  end
end
```
{: .codeblock-test #todo_list_test_1 for="todo_list" title="TodoList initializes with an empty tasks list" points="1"}

```ruby
describe "TodoList" do
  it "allows adding tasks and displays them" do
    todo_list = TodoList.new
    todo_list.add_task("Buy groceries")
    expect { todo_list.display_tasks }.to output("Buy groceries\n").to_stdout
  end
end
```
{: .codeblock-test #todo_list_test_2 for="todo_list" title="TodoList allows adding tasks and displays them" points="1"}

```ruby
describe "TodoList" do
  it "allows removing tasks that exist" do
    todo_list = TodoList.new
    todo_list.add_task("Buy groceries")
    todo_list.add_task("Walk the dog")
    todo_list.remove_task("Walk the dog")
    expect { todo_list.display_tasks }.to output("Buy groceries\n").to_stdout
  end
end
```
{: .codeblock-test #todo_list_test_3 for="todo_list" title="TodoList allows removing tasks that exist" points="1"}

```ruby
describe "TodoList" do
  it "displays a message when removing a task that does not exist" do
    todo_list = TodoList.new
    expect { todo_list.remove_task("Go to the gym") }.to output("Task not found\n").to_stdout
  end
end
```
{: .codeblock-test #todo_list_test_4 for="todo_list" title="TodoList displays a message when removing a task that does not exist" points="1"}

```ruby
describe "TodoList" do
  it "displays a message when no tasks are available" do
    todo_list = TodoList.new
    expect { todo_list.display_tasks }.to output("No tasks in the list\n").to_stdout
  end
end
```
{: .codeblock-test #todo_list_test_5 for="todo_list" title="TodoList displays a message when no tasks are available" points="1"}

```ruby
describe "TodoList" do
  it "displays each task on its own line" do
    todo_list = TodoList.new
    todo_list.add_task("Buy groceries")
    todo_list.add_task("Walk the dog")
    expect { todo_list.display_tasks }.to output("Buy groceries\nWalk the dog\n").to_stdout
  end
end
```
{: .codeblock-test #todo_list_test_6 for="todo_list" title="TodoList displays each task on its own line" points="1"}

---

- Approximately how long (in minutes) did this lesson take you to complete?
{: .free_text_number #time_taken title="Time taken" points="1" answer="any" }
