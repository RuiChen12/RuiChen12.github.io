---
layout: essay
type: essay
title: "Reflection on Software Engineering"
# All dates must be YYYY-MM-DD format!
date: 2025-05-08
published: true
labels:
  - Software Engineering
---

In this software engineering class, I didn’t just learn how to make web applications. More importantly, I learned some key ideas about software development that are useful in many kinds of projects. In this essay, I will talk about three things that helped me the most: user interface frameworks, development environments, and coding standards.

## UI Frameworks Make Development Easier

A user interface (UI) framework is a set of tools that helps developers build web pages or app interfaces faster. These tools include ready-made components, layout systems, and styling. In this course, we mainly used React-Bootstrap.

In our final project, we made a page to show club information. Here's a part of the code I wrote:

```tsx
<Row className="align-items-center mb-3">
  <Col xs="auto">
    <Image
      src={image}
      alt="Club Avatar"
      width={64}
      height={64}
      style={{
        borderRadius: '16px',
        objectFit: 'cover',
        border: '2px solid #eee',
        boxShadow: '0 1px 4px rgba(0,0,0,0.06)',
      }}
    />
  </Col>
  <Col className="text-start">
    <div style={{ fontWeight: 700, fontSize: 24 }}>{name}</div>
    <div style={{ fontSize: 16, color: '#888' }}>
      Created by:
      <br />
      {creator}
      <br />
      ({email})
    </div>
  </Col>
</Row>

With React-Bootstrap, we didn’t need to write a lot of CSS. It was much faster to build and easier to understand. I also learned that UI frameworks are not just for websites. They are used in desktop and mobile apps too, like in Electron or React Native. So this is a very useful skill.
Development Tools Help Projects Run Smoothly

A development environment is all the tools we use to write, test, and run our code. In this class, I learned how to build a full setup, including installing libraries, setting up a database, and even deploying the website.

We used npm install to install packages like React, Next.js, and Prisma. We also used PostgreSQL as our database, and Prisma helped us manage the data. For example, we used this command to set up the database tables:

npx prisma migrate dev --name init

In our final project, I learned to use Vercel to put our website online. We connected our project to GitHub, and every time we pushed new code, Vercel would build and deploy it automatically. That made the whole process much easier and faster.

Now I understand that good development tools are not just helpful—they are necessary to build and deliver a working software project.
Coding Standards Make Teamwork Better

Coding standards are a set of rules for writing code clearly and consistently. This helps team members read and understand each other’s work. In this course, we used ESLint to check our code style.

For example, if I forgot a semicolon or used double quotes instead of single quotes, ESLint would show a warning in the editor. We created a .eslintrc file to set our own rules, like using single quotes and avoiding any in TypeScript.

Here is a small example of ESLint feedback:

const x = 5 // Missing semicolon
console.log("Hello"); // Should use single quotes

During the final project, ESLint helped us make sure all the code looked the same. It saved us time when reviewing and merging code. I learned that following coding standards is not a waste of time—it actually helps the whole team work better and fix problems faster.
Conclusion

This class taught me that software engineering is more than just writing code. It’s about writing clean, organized, and maintainable code that works well with a team. From learning UI frameworks to building a full development environment to using tools like ESLint, I gained a lot of skills that I can use in many future projects. I believe these experiences will help me in my future learning and career.
