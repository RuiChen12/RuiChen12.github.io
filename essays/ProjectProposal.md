---
layout: essay
type: essay
title: "Project Proposal(TaskMatch)"
# All dates must be YYYY-MM-DD format!
date: 2025-04-01
published: true
labels:
  - Software Engineering
  - Nextjs
---



## Overview

The problem: Many students at UH Mānoa often face small but frustrating problems in daily life. For example, their computer breaks, they need help moving, or they need someone to help with design or online tasks. Usually, they go to a repair shop or try to search online tutorials. This takes time and money. On the other hand, many students have skills and time but no way to find people who need help.

The solution: TaskMatch is a web app that helps UH Mānoa students post tasks they need help with, and allows other students to take those jobs. A user can describe the task, expected pay, and time. Others can browse tasks, chat with the task creator, and accept the job. This system builds a helpful, trusted, and useful local community.

## Approach

All users must log in using their UH account to ensure safety. There are two main roles: task creators (who post jobs) and task doers (who take jobs).

Task creators can:
   -Create a new task with:
        -Task title and detailed description
        -Pay range (hourly or fixed)
        -Time range
        -Tags for needed skills (e.g., repair, tutoring, design)
        -Online/offline option
    -Get messages from interested users
    -Chat with users to confirm job details

Task doers can:
    -Browse task listings by category or filter
    -Apply to take a task
    -Chat with task creators to ask questions and confirm the job

Admins can:
    -Review flagged content
    -Create or delete skill categories
    -Ban inappropriate users

## Some mockup pages include
Main Page
    -Right side: navigation bar with:
        -Login / Register (goes to login page)
        -"Post a Task" and "Find Work" (redirects to login page if not logged in)
    -Left side: task categories such as:
        -Repair
        -Tutoring
        -Online help (e.g., game help, design, writing)
        -Moving
        -Art / Creative tasks
    -Clicking a category shows a list of related tasks with a filter panel.

Login / Register Page
    -Allows UH login or test user registration

Create Task Page
    -Form to post a new task with details, tags, pay, and timing

Browse Tasks Page
    -Filterable task list (by category, pay, date, location)

Task Detail Page
    -Full task description + “Apply” button + chat

Chat Page
    -One-on-one messages between task creator and doer

User Profile Page
    -Shows past tasks created or done, reviews, and ratings

Admin Page
    -Site moderation and task/user management
 
## Use case ideas
-A new user goes to the main page, logs in, sets up profile
-A user clicks “Post a Task,” fills out the form, and submits it
-Another user browses tasks by category, finds one, and applies
-The two users chat to confirm the details
-After task is completed, the user clicks “Mark as Done”
-Admin checks site activity, manages reported content

## Beyond the basics

After the basic features are working, we can add more:
    -Email or SMS notifications (e.g., new task match, chat message)
    -Rating and review system after each task
    -Skill badge system for active users
    -Favorite task tags and quick re-posting
    -Safety tips and in-person meeting guidelines

