---
layout: project
type: project
image: img/final.png
title: "ManoaConnect"
date: 05-08-2025
published: true
labels:
  - React
  - Next.js
  - Java
summary: "Developed a website called UH Grouping, developed and optimized web applications by using React, Next.js as front-end, Java as back-end, focusing on RESTful API integration, client-server communication, state management, and responsive interfaces."
---

<div class="text-center p-4">
  <img width="200px" src="../img/uhgrouping.png" class="img-thumbnail" >
</div>

UH Groupings is an advanced online platform designed to organize and manage groupings of individuals affiliated with the University of Hawaii. These groupings can be created based on predefined attributes such as roles (students, faculty, staff), campuses, EAC codes, or through complex combinations. Custom groupings can also be manually defined by grouping owners to address specific business or communication needs. Once established, groupings can be leveraged for various purposes, including access control to online resources, managing email distribution lists, and automating de-provisioning processes.

The platform provides robust features for administrators and developers, such as real-time synchronization with LISTSERV and Google Groups, role-based access control (RBAC), and CAS/LDAP integration for access management. Lifecycle management ensures timely and accurate removal of entitlements when users change roles or leave the university, preventing unauthorized access. Additionally, developers can utilize the Grouper API and UH Groupings tools to automate workflows and externalize application authorization logic.

As part of the UH Groupings project, I contributed to developing a modern, efficient frontend using React and Next.js, creating multiple pages to manage groupings, including toggling and resetting the inclusion and exclusion of members. The React frontend was seamlessly integrated with the backend via well-defined RESTful API endpoints, utilizing Fetch API and Promise for asynchronous data handling. The frontend supported real-time and batch operations, ensuring a responsive and scalable user experience.

I implemented advanced features, including dynamic icons with lucid-react, robust input validation powered by Zod, and custom modal dialogs and tooltips to guide users and provide real-time feedback. I integrated an asynchronous job management system to handle complex tasks such as large-scale member operations or long-running requests to ensure stability and performance under high-concurrency scenarios. Leveraging Next.js server-side rendering (SSR), I optimized data preloading and significantly improved initial page load speeds, further enhancing application responsiveness.

My primary responsibility for the Angular.js version of UH Groupings was refactoring and optimizing APIs. This involved improving the structure and logic of existing APIs and designing new endpoints to meet the evolving needs of the frontend. These new endpoints supported dynamic updates to synchronization statuses, enabling more flexible and efficient interactions. I also redefined API return types, introducing well-structured response objects that included detailed status information, such as operation result codes, updated state descriptions, and contextual information for grouping paths. This approach improved data consistency and provided additional context for frontend developers to handle complex scenarios effectively.

To ensure the reliability and stability of the refactored APIs, I developed comprehensive unit and integration tests. These tests validated critical API behaviors, such as status code accuracy, data integrity, and the successful execution of asynchronous operations, including bulk updates. Using JUnit and MockMvc, I simulated HTTP requests and verified the correctness of returned data, ensuring the system's robustness across a variety of use cases.

By combining frontend development expertise with backend refactoring and rigorous testing, I contributed to the success of UH Groupings, delivering a responsive, scalable, and user-friendly solution that streamlined grouping management across the University of Hawaii.

Here is some code that illustrates how I develop a page called preferences:

```react
const Preferences = ({ groupingPath }) => {
    const decodedGroupingPath = decodeURIComponent(groupingPath);

    const [allowOptIn, setAllowOptIn] = useState(false);
    const [allowOptOut, setAllowOptOut] = useState(false);
    const [isModalOpen, setIsModalOpen] = useState(false);
    const [modalContent, setModalContent] = useState('');
    const [loading, setLoading] = useState(false);
    const handleOptInChange = async () => {
        setLoading(true);
        const newStatus = !allowOptIn;
        try {
            const result = await updateOptIn(decodedGroupingPath, newStatus);
            if (result.resultCode === 'SUCCESS') setAllowOptIn(result.updatedStatus);
        } finally {
            setLoading(false);
        }
    };
```

You can learn more at the [UH Groupings](https://www.hawaii.edu/its/uhgroupings/).
