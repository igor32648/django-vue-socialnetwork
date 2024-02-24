# Goiaba: The Social Networking Platform
![Captura de tela 2024-02-24 093938](https://github.com/igor32648/django-vue-socialnetwork/assets/92551032/53c7d0c1-dd1d-473a-98c3-2f5222c4274b)

Goiaba is a modern and feature-rich social networking platform that enables users to connect, share, and interact in a vibrant online community. Leveraging the power of Django 5.0.2 and Vue.js 3.4.1, Goiaba offers a seamless user experience with a plethora of functionalities tailored for today's social media enthusiasts. The design is crafted with Tailwind CSS 3.4.1, ensuring sleek and intuitive user interfaces.

## Features

### User Profiles


- **Create Profiles:** Users can easily create personalized profiles with customizable details and profile pictures.

![Captura de tela 2024-02-24 094039](https://github.com/igor32648/django-vue-socialnetwork/assets/92551032/59d5609d-cf76-44f8-b283-698882783116)

- **Profile Management:** Users have full control over their profiles, including editing personal information and updating profile pictures.

### Social Connectivity

![Captura de tela 2024-02-24 093602](https://github.com/igor32648/django-vue-socialnetwork/assets/92551032/f5b9bdbb-42be-418f-870b-fcc4df014ea6)

- **Friendship Management:** Users can add, remove, and manage friends within the platform.

![Captura de tela 2024-02-24 113258](https://github.com/igor32648/django-vue-socialnetwork/assets/92551032/247438aa-e008-461c-a5cc-fe8d14ef5948)

- **Friend Recommendations:** Socialite intelligently suggests potential friends based on common interests and connections.

![Captura de tela 2024-02-24 093321](https://github.com/igor32648/django-vue-socialnetwork/assets/92551032/581535c6-4509-4515-8e4a-4a7029fa51a7)

- **Friend Notifications:** Receive notifications when new friend requests are sent or accepted.

![Captura de tela 2024-02-24 113246](https://github.com/igor32648/django-vue-socialnetwork/assets/92551032/5b739bcc-dfd8-4cfa-ae43-a3df3fa9e335)

- **Like Posts:** Users can express their appreciation by liking posts made by friends.

### Content Sharing


- **Post Creation:** Users can share their thoughts, experiences, and photos by creating posts.

![Captura de tela 2024-02-24 112234](https://github.com/igor32648/django-vue-socialnetwork/assets/92551032/702d259a-c359-4fc8-8749-60f9e40215ec)

- **Commenting:** Engage in conversations by commenting on posts made by friends.
- **Media Sharing:** Share photos and images to express yourself visually.


- **Notification System:** Get notified of new interactions, including comments on your posts, friend requests, and post likes.

### Private Communication

![Captura de tela 2024-02-24 094143](https://github.com/igor32648/django-vue-socialnetwork/assets/92551032/0bb9995f-72e3-4fca-9147-554fe6308968)

- **Private Messaging:** Send and receive private messages to communicate directly with friends. Enjoy real-time private conversations with friends in a secure and private chat environment.

![Captura de tela 2024-02-24 112739](https://github.com/igor32648/django-vue-socialnetwork/assets/92551032/a076e258-2ce7-4074-98c5-472b6453c93f)
![Captura de tela 2024-02-24 112756](https://github.com/igor32648/django-vue-socialnetwork/assets/92551032/d7516c33-9e1c-4dea-a5ad-b4b6158b3128)

- **Private Posts:** Goiaba empowers users with the ability to choose the privacy settings for their posts, enabling them to decide whether a post should be public or visible only to friends. This feature provides advantages such as content control, selective sharing, a customized experience, and enhanced privacy, fostering a safer and more personalized social networking environment.

## Features Powered by Python Scripts

![Captura de tela 2024-02-24 094117](https://github.com/igor32648/django-vue-socialnetwork/assets/92551032/7757c76a-b839-4463-874b-ad4ec2a2c62a)

### Trending Topics and Suggested Friends
- **Trending Topics:** The platform dynamically identifies and displays trending topics using Python scripts running in the backend. These scripts analyze user interactions and post content to determine the most popular discussions across the platform.
- **Suggested Friends:** Socialite provides personalized friend recommendations by running Python scripts in the backend. These scripts utilize algorithms to suggest potential friends based on common interests, mutual connections, and user activity patterns.

![Captura de tela 2024-02-24 094756](https://github.com/igor32648/django-vue-socialnetwork/assets/92551032/7eea4c81-ce3d-439d-b844-c529d25403ff)

The utilization of Python scripts in the backend enhances the platform's functionality by delivering real-time insights and recommendations to users, fostering engagement and community growth.

### Responsive Design
![Captura de tela 2024-02-24 103740](https://github.com/igor32648/django-vue-socialnetwork/assets/92551032/eaabc408-454c-4632-9566-b5c449ce0981)
![Captura de tela 2024-02-24 103808](https://github.com/igor32648/django-vue-socialnetwork/assets/92551032/b4015d6e-bffb-4c26-b52a-4c16724707f9)
![Captura de tela 2024-02-24 103822](https://github.com/igor32648/django-vue-socialnetwork/assets/92551032/0003ef43-6de1-40df-8ee9-878028a2342f)

- **Mobile-Friendly:** Socialite features a responsive design, ensuring seamless user experience across various devices, including smartphones and tablets.
- **Adaptable Layout:** The interface adapts gracefully to different screen sizes, maintaining usability and aesthetics.

## Dependencies

### Frontend
- **Vue.js (Version 3.4.1):** A progressive JavaScript framework used for building user interfaces. The latest version was utilized for enhanced performance and feature support.
- **Vite (Version 5.0.11):** A fast build tool for modern web development. Vite was employed to streamline the development process and improve project efficiency.
- **Tailwind CSS (Version 3.4.1):** A utility-first CSS framework that provides a set of pre-designed components and utilities, allowing for rapid and consistent styling across the application.

### Backend 
- **Django Framework:** Goiaba backend was developed using Django version 5.0.2. 
- **rest_framework:** Django REST framework for building Web APIs.
- **rest_framework_simplejwt:** Provides JSON Web Token authentication support for Django REST framework.
- **corsheaders:** Handles Cross-Origin Resource Sharing (CORS) to allow secure communication between the backend and frontend components.

## Project Foundation and Customization

Goiaba was built based on the 12-hour tutorial series by Code With Stein on YouTube, but also underwent custom enhancements to ensure a seamless user experience. These enhancements include optimizing all screens for mobile devices and tweaking the UI with modified button styles and design elements, enhancing usability and visual appeal.

### Planned Features
1. **Dark Mode:** Implement an option for users to switch between light and dark themes to enhance accessibility and user experience, catering to varying preferences and environments.
2. **Splash Screen:** Develop a welcoming splash screen to appear before the login screen, providing users with essential information about the platform, promotions, or updates, and enhancing the overall user onboarding experience.

## Installation and Running the Code

### Installation
1. Clone the repository: `git clone https://github.com/igor32648/django-vue-socialnetwork.git`
2. Navigate to the backend directory: `cd django_goiaba`
3. Install backend dependencies: `pip install -r requirements.txt`
4. Navigate to the frontend directory: `cd vue_goiaba`
6. Install frontend dependencies: `npm install`

### Running the Code
7. Start the Django server at the backend directory: `python manage.py runserver`
8. Start the Vue frontend at the frontend directory: `npm run server`
9. Access the application at `http://localhost:5173` in your web browser.

## Running Database Scripts

To update the trending topics and friend suggestions in the database, follow these steps:

1. Open your terminal.
2. Navigate to the backend directory of the project: `cd django_goiaba`
3. Run the following commands:
   ```
   python scripts/generate_friend_suggestions.py
   ```
   This command will generate friend suggestions based on user interactions and activity patterns.

   ```
   python scripts/generate_trends.py
   ```
   This command will generate trending topics by analyzing post content and user interactions.

4. After running these commands, the database will be updated with the latest trending topics and friend suggestions, enhancing the user experience on the platform.

It's recommended to run these scripts periodically to keep the trending topics and friend suggestions up to date.
