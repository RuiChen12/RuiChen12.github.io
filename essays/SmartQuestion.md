---
layout: essay
type: essay
title: "Smart Questions, Good Answers"
# All dates must be YYYY-MM-DD format!
date: 2015-09-08
published: false
labels:
  - Questions
  - Answers
  - StackOverflow
---

<img width="300px" class="rounded float-start pe-4" src="../img/smart-questions/rtfm.png">

## Is there such thing as a stupid question?

In the world of software development, smart questions are essential for smart software engineers. Engineers have limited time and energy, so they prefer to invest in well-formed, valuable questions rather than decipher vague or poorly structured help requests. A well-crafted question clearly expresses the problem, provides enough context for a quick diagnosis, and demonstrates the questioner's effort—rather than forcing the answerer to guess what’s wrong. However, many people do not know how to ask questions effectively, leading to their queries being ignored or even causing frustration among experienced developers. Asking technical questions is a skill that must be mastered in developer communities and forums, as a good question not only helps the asker receive precise and useful answers but also benefits future developers who encounter the same issue. Poorly structured questions, on the other hand, can confuse or irritate potential answerers, reducing the likelihood of getting help. So, how can we ask smart questions?

## What’s a smart question?

There are several core features of smart questions:

    1. Clear title: The title should accurately describe the problem, rather than asking a general question like "Can anyone help me?"

    2. Show your attempts: Showing the code you have tried and the documents you have studied can make it easier for the answerer to understand your problem.

    3. Provide enough information: Include your development environment, error messages, code snippets, etc., so that others can effectively help you troubleshoot the problem.

    4. Be polite and respectful: Although technology is more important than politeness, proper politeness can increase the possibility of getting help.
    
In the following example, we will analyze a real-world example of a coding question regarding a "todos.map is not a function" error in a React application.

```
Q: Getting data.map is not a function

import { useState, useEffect } from "react";
import { TodoProvider } from "./contexts/TodoContext";
import TodoForm from "./components/TodoForm";
import TodoItem from "./components/TodoItem";

function App() {
  const [todos, setTodos] = useState([]);

  const addTodo = (todo) => {
    setTodos((prev) => [{ id: Date.now(), ...todo }, ...prev]);
  };

  const updateTodo = (id, todo) => {
    setTodos((prev) =>
      prev.map((prevTodo) => (prevTodo.id === id ? todo : prevTodo))
    );
  };

  const deleteTodo = (id) => {
    setTodos((prev) => prev.filter((prevTodo) => prevTodo.id !== id));
  };

  const toggleComplete = (id) => {
    setTodos((prev) =>
      prev.map((prevtodo) =>
        prevtodo.id === id
          ? { ...prevtodo, completed: !prevtodo.completed }
          : prevtodo
      )
    );
  };

  useEffect(() => {
    const todosLocal = JSON.parse(localStorage.getItem("todos"));

    if (todosLocal && todosLocal.length > 0) {
      setTodos(todosLocal);
    }
  }, []);

  useEffect(() => {
    localStorage.setItem("todos", JSON.stringify("todos"));
  }, [todos]);

  return (
    <TodoProvider
      value={{ todos, addTodo, updateTodo, deleteTodo, toggleComplete }}
    >
      <h2 className="text-center text-3xl font-bold mt-1">Hello</h2>
      <div className="bg-[#172842] min-h-screen py-8">
        <div className="w-full max-w-2xl mx-auto shadow-md rounded-lg px-4 py-3 text-white">
          <h1 className="text-2xl font-bold text-center mb-8 mt-2">
            Manage Your Todos
          </h1>
          <div className="mb-4">
            {/* Todo form goes here */}
            <TodoForm />
          </div>
          <div className="flex flex-wrap gap-y-3">
            {todos.map((todo) => (
              <div key={todo.id} className="w-full">
                <TodoItem todo={todo} />
              </div>
            ))}
          </div>
        </div>
      </div>
    </TodoProvider>
  );
}

export default App;

I'm getting error todos.map is not a function, only that line gives error if I remove the div of the mapping then the code works fine. All the other functions and components works fine, then why is this not working.

Please someone explain this, todos is an array then why the mapping is not working here.
```

On Stack Overflow, the question "todos.map is not a function" is an example that partially meets the standards of a smart question. The asker clearly identifies the specific error message, todos.map is not a function, and describes the conditions under which the issue occurs. They also provide a portion of the code, showing how the data is retrieved rather than just describing the error. Additionally, the asker expresses their confusion—todos is supposed to be an array, yet the .map() function does not work—demonstrating that they have engaged in some logical reasoning before posting the question. However, the question still has several shortcomings that prevent responders from providing efficient assistance.

First, the title is too vague—it only states the error message without specifying the context in which the error occurs. A better title would be something more specific, such as "todos.map error in React useEffect, possibly related to localStorage", which would immediately indicate to responders that the issue may be connected to useEffect or localStorage. Second, the asker assumes that todos is an array but does not provide debugging information, such as console.log(todos), to confirm this assumption. Since data stored in localStorage is by default a string, the asker should first verify the data type instead of relying solely on intuition. Additionally, the asker does not realize that the line localStorage.setItem("todos", JSON.stringify("todos")) actually stores the string "todos" rather than an array. If localStorage.getItem("todos") returns a string, directly using JSON.parse() to parse it could lead to an unexpected data format, causing the .map() error. Finally, the asker mentions that "removing the <div> allows the code to work," but does not explain how <div> might affect the execution of todos.map(). This lack of clarity makes it difficult for responders to provide a comprehensive answer.

```
A: 

My guess is the problem is you're assuming that localStorage is an array.

const todosLocal = JSON.parse(localStorage.getItem("todos"));

    if (todosLocal && todosLocal.length > 0) {
      setTodos(todosLocal);
    }

You need to check if todosLocal is an array, not just has a length.

so:

if (Array.isArray(todosLocal) && todosLocal.length > 0) ...

```
 
Nevertheless, the community still provided some effective answers. One of the respondents identified the core issue: localStorage.getItem("todos") might return a string instead of an array, which prevents .map() from functioning. They suggested that the asker should check whether todosLocal is an array rather than just checking its length. However, while this answer points out the problem, it is not particularly efficient.

If the asker had provided a more detailed description in the question, such as "I am using useEffect in React to retrieve todos from localStorage and then attempt to iterate over it with .map(), but I am encountering a todos.map is not a function error. If I remove the <div>, the code runs fine. All other functions and components are working properly." and further asked "Why is todos not an array? Why does the error disappear when I remove the <div>? How should I correctly store and retrieve array data from localStorage?", the responses might have been more precise and helpful.

For example, a respondent might have guided the asker to debug the issue using console.log(todosLocal) to directly verify the data type. Additionally, the respondent could have pointed out that localStorage.setItem("todos", JSON.stringify("todos")) is an incorrect way to store the data and explained the proper method—storing an actual array using JSON.stringify(todos), rather than the string "todos".

This case illustrates that an unclear question can prevent respondents from providing the most effective assistance. While the asker received a partially helpful response, a more complete background in the question could have led to a more precise and efficient solution, reducing unnecessary back-and-forth communication. It also highlights the importance of asking smart questions in technical communities—well-formed questions are more likely to capture the attention of experts and lead to faster problem resolution, whereas unclear questions can result in inefficient discussions or even be ignored entirely.

## The foolproof way to get ignored.

While there are decent questions that benefit everyone, there are those one can ask to create an entirely different effect. In the following example, a user asks how he would, in short, create a desktop application with Facebook.

```
Q: Facebook Desktop Notifier

I am a beginner programmer that have never used anything other than what's included in a language.

I am trying to create a desktop application that notifies me anytime I get an update onfacebook. 
How should go about doing this? Thanks in advance.

edit Sorry I was not clear. Is there any way to make a DESKTOP application with facebook?
```

A simple “yes” would have answered the question, but we know that’s not the sort of answer he or she is looking for. Fortunately, someone kindly responded with a link to Facebook’s developer website. The asker should have done more research on his or her potential project. Then further down the road, he or she could have asked more specific and detailed questions that wouldn’t require a thousand-paged response for a sufficient answer.

## Conclusion

When we rely on others’ generosity and expertise to provide answers to our questions, it should hold that the question we ask should be one that leads to efficient and effective help that not only benefits us, but also the people we ask and others who might ask the same question in the future. Thus, if you have a question… make it a smart one! Asking questions may not always get you the best answer, but asking them in a way that will make others want to answer them will increase the success of finding a good solution and make it a positive experience on all sides.
