---
layout: essay
type: essay
title: "Ai Use Reflection"
# All dates must be YYYY-MM-DD format!
date: 2025-05-08
published: false
labels:
  - Questions
  - Answers
  - AI
---
## I. Introduction

In recent years, artificial intelligence (AI) has changed how many people learn. In education, AI can be used to explain topics, help with writing, and even build projects. In software engineering, tools like ChatGPT and GitHub Co-Pilot have helped students and developers fix bugs, write code, and learn faster.

In ICS 314, I mainly used **ChatGPT** to help me write code, fix bugs, and understand concepts. I didn’t use tools like Bard or Claude, and I only tried GitHub Co-Pilot a few times. ChatGPT was my main tool, and I used it often in this class.

## II. Personal Experience with AI

Here are some examples of how I used AI (or didn’t) for each part of ICS 314:

- **Experience WODs (e.g. E18)**  
  In the beginning, for WODs like E18, I didn’t use AI at all. These tasks mostly involved basic JavaScript and simple logic, so I could do them by myself.  
  But later, when we started learning functional programming, I got confused with some functions. For example, in one WOD, I wasn’t sure if I should use `_.filter` or `_.map`, or how to combine them. So I asked ChatGPT:  
  > “How do I use the filter and map together in underscore?”  
  It showed me an example and helped me understand how to use them together. Still, I didn’t always use AI because these WODs didn’t affect my grade, and sometimes I liked solving the problems on my own.

- **In-class Practice WODs**  
  At first, I didn’t use AI because the practice WODs were just basic JavaScript. But once we started using React components, I needed help more often.  
  For example, when I was making a webpage, I asked ChatGPT how to move the address next to the email inside the footer using CSS. It gave me a small code example and explained how to do it.  
  Sometimes I still tried to finish without AI just to test myself—especially when I already had an idea of what to do.

- **In-class WODs**  
  I used AI in almost every in-class WOD. Since these were timed, I wanted to finish quickly and get a good score. AI helped me complete things faster.

- **Essays**  
  I used ChatGPT to help organize my ideas and improve my grammar.  
  For example, before writing the ethics essay, I asked:  
  > “Can you give me an outline for this essay?”  
  After writing some paragraphs, I asked:  
  > “Can you help me rewrite this to make it more clear?”  
  Because English is my second language, AI helped me express myself better. But I always made sure the ideas and structure were my own.

- **Final project**  
   I used AI a lot for the final project. Some things, like passing data between pages in Next.js using props and query parameters, were not fully taught in class.  
  I asked ChatGPT:  
  > “How do I pass props using Link in Next.js?”  
  It helped me build code like this:

```
<Link
  href={
    pathname: '/clubs/profile',
    query: {
      name: club.name,
      description: club.description,
      image: club.image,
      creator: club.creator,
      email: club.email,
    },
  }
>
```
  I also used AI when I had bugs in the React state or layout issues in the UI.
- **Learning a concept/tutorial**  
  I didn’t use AI to learn the basic concepts. When I studied the official tutorials for React, TypeScript, or HTML, I wanted to focus and learn from the source.
  I thought that if I always used AI for this, I might not fully understand the fundamentals. So I read the docs and tried things by myself.
  
- **Answering a question in class or Discord**
  I didn’t use AI to answer questions. I felt like if I could solve the problem, I should answer it myself. Also, if someone else asked a question, they could ask AI too—so I didn’t see the        point in using it for that.
  
- **Asking or answering a smart question**
  I didn’t use AI here either. I didn’t do this very often, but when I did, I tried to rely on what I had already learned.

- **Coding examples**
  I used AI often to find simple examples, especially when I forgot the syntax.
  For example, I asked how to use a forEach loop or how to use some functional programming functions. It saved time and helped me review.
  
- **Coding examples**
  Sometimes I copied code from AI but didn’t fully understand it. So I asked ChatGPT to explain things like:

    “What does query do in a Next.js Link?”
    or
    “What happens when useEffect has an empty dependency array?”
    These answers helped me understand how data flows in React and how re-rendering works.
  
- **Writing code**
  Yes, I used AI when writing code, especially small components or logic functions.
  For example, I asked:

    “How do I create a simple modal in React-Bootstrap?”
    AI gave me a basic example, and then I changed it to match our project’s style. I always tested the code and checked it before using it.

- **Documenting code**
  I didn’t use AI to write comments. I wanted to practice explaining my logic clearly.
  In our final project, I wrote things like:
  // This function opens the modal when the edit button is clicked
  Writing my own comments helped me think more deeply about what the code was doing.

- **Quality assurance**
  This was one of the most helpful uses of AI for me. Many times, I got strange ESLint or runtime errors. I copied the error and asked ChatGPT:

    “Why am I getting 'property undefined' when accessing an image in a club object?”
    It explained that maybe the object wasn’t loaded yet, and I should check for null.
    I also asked during Prisma errors:
    “Why is my migration failing with a relation error?”
    ChatGPT helped me figure out I had a mistake in my schema file.

- **Other uses**
  I don’t remember using AI for anything else. Mostly, I used it for debugging, writing code, and learning harder parts of React.
## III. Impact on Learning and Understanding

AI helped me learn faster. It explained things I didn’t understand, especially with React and Next.js. I think many students use AI for the same reason: it’s like having a tutor who is always available.

But sometimes I worry that I rely on it too much. If I always ask ChatGPT, I might forget how to solve problems on my own. So I try to use AI only when I need help.


## IV. Practical Applications

Outside of class, I also used AI in my job. I work with React and Angular, and sometimes my CSS or icons don’t show up correctly. I ask AI, “Why is this image not centered?” or “How do I change the font size in CSS?” and it helps me fix things.

However, when I ask AI to generate full code, it sometimes doesn’t work with my current project. So I only use it for bug fixes or quick help, not full solutions.

## IV. Challenges and Opportunities
Sometimes AI gave me answers that didn’t work. For example, in our final project, we couldn’t figure out why a form wasn’t submitted. AI didn’t help much. Later, we found the problem was a small .url() string in a different file. This showed me that AI can’t always solve everything. However, I think AI still has many learning opportunities. It can be used to help students break down big problems, and even give feedback on their code.

## VI. Comparative Analysis
Traditional teaching is sometimes limited. For example, during the final project, the class content didn’t help with everything, so I used Google. AI is like a smarter version of Google—it gives you answers faster and with more explanation.

But traditional methods are more strict and help you remember things better. AI is fast, but sometimes not deep. I think the best way is to use both together: teachers explain the hard parts, and AI helps when you’re stuck.

## VII. Future Considerations

In the future, I think AI will become even more common in education. Maybe AI will write perfect code that fits your whole project. But that also means programmers will need to understand deeper skills—things AI can’t do yet.

The challenge is: that if AI gets too good, students might not learn enough. But if we learn how to use it wisely, AI can make education better for everyone.


## VIII. Conclusion

AI helped me a lot in ICS 314. It explained errors, helped me understand web development, and made me more confident in solving problems. But I also learned to be careful and not rely on it too much. In the future, I hope classes can teach us how to use AI in smart ways—like how to ask good questions and understand the answers. AI is a great tool, but learning how to think is still the most important part.



AI is being used to help with grammar

