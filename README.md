# Welcome to Our Django Hotel Management System!

Welcome to our comprehensive Django Hotel Management System! We're thrilled to have you on board. Whether you're a hotel manager, staff member, or developer, this system is designed to streamline your operations and enhance guest experiences.

# User Experience (UX)

## For Hotel Staff:

- Efficient Workflow Management
  Hotel staff can navigate through daily tasks effortlessly with our user-friendly interface. From managing bookings to handling room assignments, each step of the workflow is streamlined for maximum efficiency.

- Personalized Guest Service
  Our system empowers staff to provide personalized experiences for guests. With easy access to guest preferences, special requests, and feedback history, staff members can anticipate needs and exceed expectations.
  
- Insightful Analytics
  Hotel managers gain valuable insights into performance metrics, occupancy rates, and revenue trends through comprehensive analytics tools. This data-driven approach enables informed decision-making and strategic planning.

## For Guests

- Seamless Booking Experience
  Guests enjoy a hassle-free booking process with our intuitive reservation system. Whether booking online or through the front desk, the process is quick, secure, and tailored to individual preferences.
  
- Exceptional Service
  From check-in to check-out, guests receive attentive and personalized service from hotel staff. Special requests and preferences are seamlessly integrated into the guest experience, ensuring a memorable stay.
  
- Convenient Access
  Our system offers guests convenient access to essential information and services, such as room availability, amenities, and local attractions. With a user-friendly interface, guests can easily navigate and make the most of their stay.





# Features

## 1. Booking Management
Effortlessly handle room reservations, check-ins, and check-outs with our intuitive booking management system. From single bookings to group reservations, streamline the entire process for maximum efficiency.

## 2. Inventory Control
Maintain full control over your hotel's inventory, including room availability, rates, and special packages. Easily adjust pricing, manage room allocations, and track inventory in real-time.

## 3. Guest Relations
Deliver exceptional guest service with personalized experiences tailored to individual preferences. Access guest profiles, manage special requests, and gather valuable feedback to enhance guest satisfaction.

## 4. Financial Tracking
Stay on top of your hotel's financial health with comprehensive financial tracking tools. Monitor revenue, expenses, and billing transactions to ensure accurate accounting and financial management.

## 5. Admin Dashboard
Access a centralized dashboard with insightful analytics, reports, and administrative tools. Gain valuable insights into occupancy rates, revenue trends, and guest demographics to inform strategic decision-making.

## 6. Customization Options
Tailor the system to your hotel's unique requirements with flexible customization options. From branding and theme customization to configuring user permissions, adapt the system to suit your specific needs.

## 7. Security Measures
Ensure the security of guest data and sensitive information with robust security measures. Implement encryption, access controls, and regular security audits to protect against potential threats.

## 8. Mobile Compatibility
Access key features of the system on the go with mobile compatibility. Whether on a smartphone or tablet, stay connected and manage hotel operations from anywhere, at any time.



# Testing

## Manual Testing:

### Functional Testing
 - Booking Process: Manually test the booking process to ensure that guests can make reservations smoothly, and staff can manage bookings effectively.
 - User Authentication: Verify that user authentication mechanisms, such as login and registration, function correctly and securely.
 - Room Management: Test the functionalities related to room management, including adding, editing, and deleting rooms.
 - Guest Services: Validate that guest services, such as room service requests and housekeeping, are working as expected.
### Usability Testing
 - User Interface: Evaluate the user interface for intuitiveness, clarity, and consistency, ensuring that users can navigate the system with ease.
 - Accessibility: Test the system's accessibility features to ensure compliance with accessibility standards and accommodate users with disabilities.
 - Error Handling: Assess how the system handles errors and edge cases, providing informative error messages and guiding users to resolve issues.

### Compatibility Testing
 - Browser Compatibility: Test the system across different web browsers (e.g., Chrome, Firefox, Safari) to ensure consistent functionality and appearance.
 - Device Compatibility: Validate the system's performance on various devices, including desktops, laptops, tablets, and smartphones, to accommodate users across different platforms.

## Bugs/Unfixed Bugs:
- Fixed: When creating my apps, I decided I needed to separate my models for member details from the class details and booking models in a separate app. I changed the name of my original 'book' app to 'member' as this already contained my Member and MemberLogin models that had been migrated to the database and deployed on Heroku. I followed the steps and successfully changed the name of the app by utilizing the [django-rename-app](https://github.com/odwyersoftware/django-rename-app?tab=readme-ov-file).

- Fixed: When implementing Django signals into the "member" app when trying to create a user profile for each user that signs up, I received the following error: django.core.exceptions.ImproperlyConfigured: Application labels aren't unique, duplicates: member . After researching, I was able to fix the problem my removing the 'member' in INSTALLED_APPS of the Settings file. This was found using [Stack Overflow](https://stackoverflow.com/questions/24319558/how-to-resolve-django-core-exceptions-improperlyconfigured-application-labels).

- Fixed: I ran into a bug when trying to implement the class cancellation function. Daisy helped debug and I now understand that Django provides built-in primary keys, where I had overidden the automatic PK with booking_id. Once I implemented the correct key into the code, it works well.

- Unfixed: When testing my .py files with the CI Python Linter, this line was proven to be too long. However, even after adding parentheses and entering to the next line and trying multiple options, I was unable to fix the result 'continuation line with same indent as next logical line': 
    if selected_datetime.strftime('%A %H:%M') not in available_options[booked_class.class_name]:   

    The same issue occured with this path, however I was unable to fix and feared ruining my url path:
        path('cancel/booking/<int:booking_id>/', cancel_booking, name='cancel_booking'),

    Same issue with this line:
        return f"{self.member} booked {self.booked_class} on {self.class_date} beginning at {self.class_time}."

# Deployment

## Steps taken to deploy on Heroku:

### Set up the workspace:

 - Install gunicorn: Gunicorn is a Python WSGI HTTP Server for UNIX, required for Heroku deployment. Install it in your workspace using pip install gunicorn.
 - Update requirements.txt and create Procfile: Ensure that gunicorn is added to your requirements.txt file. Create a Procfile in the root directory of your project and add the following line: web: gunicorn <hotel_management>.wsgi --log-file -.
 - Set DEBUG to False: In your Django project's settings.py, set DEBUG = False to ensure that your application runs in production mode.
 - Git add, commit and push changes to GitHub: Add any changes you've made, commit them, and push them to your GitHub repository.

### Deploy on Heroku:

 - Create the app on Heroku and connect to GitHub project: Log in to your Heroku account, navigate to the dashboard, and create a new app. Connect your Heroku app to your GitHub repository under the "Deploy" tab.
 - Set Config Vars in the "Settings" Tab: Go to the "Settings" tab of your Heroku app. Under the "Config Vars" section, set any necessary environment variables required for your Django application, such as SECRET_KEY, DATABASE_URL.
 - Deploy the app: Navigate to the "Deploy" tab on your Heroku dashboard. Scroll down to the "Manual deploy" section and click on "Deploy Branch". Heroku will then fetch the latest code from your GitHub repository and start the deployment process.
 - Verify deployment: Once the deployment process is complete, Heroku will provide you with a URL where your application is now live. You can visit this URL to verify that your Django application is running correctly on Heroku.


## Clone Repository

Cloning a repository allows you to create a local copy of it on your machine:

 - Within GitLab, navigate to the repository you want to clone.
 - Look for the "Clone" button, usually located on the right side of the repository page.
 - Click the "Clone" button and copy the HTTPS or SSH URL provided.
 - In your terminal or Git Bash, navigate to the directory where you want to clone the repository.
 - Type 'git clone' followed by the URL you copied from GitLab. For example:
    git clone https://gitlab.com/username/repository.git
 - If you're using SSH, you'd use an SSH URL instead.
 - Press Enter. Git will clone the repository onto your local machine.
 - You may be prompted to enter your GitLab credentials if you haven't authenticated previously.
 - Once the clone process is complete, you'll have a local copy of the repository in the directory you specified.

# Credits

### Code
 - To help me get started with the project and understand the basics, i followed Code Institute and Matt´s Walktrough on "I Think therefore i Blog", big thanks for getting me started.

 - Ed, Ger and Oisin, Tutors at Code Institute helped me solve some bugs in my code, big thanks.

### Bootstrap
 - Bootstrap has an amazing library and has helped me focus on the backend and save a lot of time with style, and layout on the frontend.

### Django
 - The generic views from Django made my life much easier, also great documentation.

### Issues with code
 - Most of the daily problems were solved thanks to Stackoverflow and W3Schools.


### Technologies Used
- Figma = Wireframes
- Django = Framework
- HTML = mark up language
- CSS = styling
- [Bootstrap 4.6](https://getbootstrap.com/docs/4.6/getting-started/download/) = styling
- Python = functionality
- VS Code = IDE
- Heroku = Deployment
- GitHub = Used to store the project
- Git = version control
- ElephantSQL
- [TinyPNG](https://tinypng.com/) used to compress images

# Acknowledgment
We would like to express our gratitude to the following individuals and organizations for their invaluable contributions to the development and success of our Django Hotel Management System:

 - Open Source Community: We are indebted to the vibrant open-source community for their continuous support, inspiration, and contributions to the Django framework and related technologies.
 - Django Developers: Our heartfelt thanks to the developers of Django for creating a powerful, flexible, and scalable web framework that serves as the foundation for our hotel management system.
 - Contributors: A special acknowledgment to all the contributors who have dedicated their time, expertise, and effort to enhance the functionality, usability, and reliability of our system through code contributions, bug reports, and feature suggestions.
 - Beta Testers: We extend our appreciation to the beta testers who volunteered to test early versions of the system, providing valuable feedback and insights that helped us identify and address issues before the official release.
 - Stack Overflow Community: We are grateful to the Stack Overflow community for providing invaluable assistance and solutions to technical challenges encountered during the development process.
 - Documentation Contributors: Our thanks to those who have contributed to the documentation efforts, helping to create clear, comprehensive, and user-friendly guides for installation, usage, and troubleshooting.

We deeply appreciate the collective effort and collaboration that have made our Django Hotel Management System possible. Your support and contributions are truly appreciated!
