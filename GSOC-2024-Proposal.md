"Creating a brazilian boilerplate of a digital participation platform" proposal for
Google Summer of Code 2024
================

Table of content
================

1. **Introduction**

    1.1 About the Organization

    1.2 About the Project

2. **Abstract**

    2.1 The existing platform

    2.2 Goals - The Boilerplate

    2.3 Benefits

3. **Proposal Timeline**

    3.1 Bonding Period

    3.2 Official Coding Period

4. **About me**


# 1 Introduction

## 1.1 About the Organization

LAPPIS, a Brazilian FOSS lab led by women, is dedicated to fostering collaboration and engagement in OSS. Our mission is to increase the participation of young South Americans, women, and other underrepresented groups in high-impact open-source projects. We aim to overcome barriers such as language, impostor syndrome, and inclusion.
We have established several OSS local communities, including one focused on a chatbot architecture trained in Portuguese and another on a social participation app called "Empurrando Juntas." This app collects opinions and utilizes artificial intelligence techniques to group participants based on their views.
Our flagship project, "Brasil Participativo," is a collaboration with the federal government and the Brazilian Decidim Community, serving as Brazil's digital participation platform. In just one year, the platform has engaged over 1.5 million active participants, making it the largest online social participation initiative orchestrated by the government in Brazil. Developed using Decidim, an open framework for citizen participation, the platform includes machine learning modules for recommendations and moderation.
Brasil Participativo, powered by Decidim, enables national councils, ministries, and federal agencies to conduct inclusive public consultations. This creates a space for citizens to actively contribute to the formulation of decrees, ordinances, and other critical actions. Decidim, managed by the Decidim Free Software Association, serves as the democratic backbone of this initiative, empowering communities and fostering a culture of collaborative governance.
As we look to the future, Brasil Participativo, fueled by Decidim, remains a beacon of digital empowerment. It invites individuals to create profiles and actively engage in shaping the policies that affect their lives.
Engaging individuals from diverse backgrounds in participation platforms is a global challenge. This involves offering clear and meaningful participatory processes that address people's everyday problems. It's also essential to simplify the choice architectures so participants can easily understand how to contribute, reducing barriers such as the number of clicks and the complexity of interfaces.
Other challenges include addressing performance issues with the Decidim platform, simplifying the user experience, implementing new features, and utilizing machine learning modules for monitoring guidance.


## 1.2 About the project

One critical prerequisite for the Brasil Participativo platform is to ensure universal citizen participation. This presents a significant technopolitical challenge in a country marked by pronounced social and educational disparities, where various segments of the population face obstacles in engaging with virtual environments. In recent years, there has been a growing interest in participatory platforms that enable organizations to engage with their communities effectively. These platforms facilitate two-way communication, allowing organizations to gather feedback, crowdsource ideas, and collaborate with their stakeholders. Building on the success and experience of the Brasil Participativo initiative, we propose to develop a boilerplate that will enable organizations to create their own participatory platforms easily.
The project will focus on creating a basic boilerplate that includes essential features such as user authentication, participatory spaces, user experience. The boilerplate will be designed to be scalable and extensible, allowing organizations to add additional features as needed. By developing a participatory platform boilerplate based on Brasil Participativo, we aim to empower organizations to engage with their communities in a meaningful and impactful way. This project aligns with our commitment to promoting transparency, inclusivity, and democratic participation. Some tasks necessary:
Develop a customizable and easy-to-deploy boilerplate based on the principles and features of Brasil Participativo. Provide organizations with a tool to create participatory platforms tailored to their needs.
Promote transparency, engagement, and collaboration between organizations and their stakeholder.

Possible mentors: @LeoSilvaGomes @rocha.carla

Expected size of the project: 350 hours

# 2 Abstract

## 2.1 The existing platform
The current version of the platform was designed to serve a national scenario, and this makes it difficult to customize for use, for example, by other organizations or even at a state or local level. Therefore, despite the aim of reaching as many people as possible, its level of complexity makes this unfeasible.

## 2.2 Goals - The Boilerplate
The objective of this project is to develop a boilerplate that will simplify the development of a participatory platform, which should serve any type of organization, facilitating its initial configuration, and the customization of projects and discussions that will be made available.
As we are dealing with limited time for project development, it is extremely important to define which parts of the original Decidim will be prioritized, and maintain focus on the main features and customization.

## 2.3 Benefits
A "Participatory Brazil" boilerplate will make it possible for organizations from all spheres to have their participatory platforms, creating environments that value communication and democracy in their decision-making, bringing visibility and inclusion to everyone who wants to contribute and give their opinion. Facilitating the creation of participatory platforms can encourage organizations to have a transparency portal, providing a channel that generates engagement and communication with society.

# 3 Proposal Timeline

## 3.1 Bonding Period 

### 3.1.1 Before March 29:
Familiarize myself completely with Ruby and Rails Framework, study the Brasil Participativo Platform, the functionalities and architecture of Decidim, and participate in the community solving and issue.

### 3.1.2 April 02 – May 01 (Before the official coding time):

Improve my further understanding and ease of use with Rails ORM and database(PostgreSQL).
During this period I will remain in constant touch with my mentors and the community remaining active on the community communication channels.

## 3.2 Official Coding Period

### 3.2.1 May 01 – May 26

Read documentation and prepare to work on the project, make the modifications, if any, that needs to be on existing schemas and design of new schemas (if needed to fit cleanly with Decidim and Brasil Participativo Architecture).Thus with the help of my mentor I will become absolutely clear about my future goals,the final database implementations that need to be done as well as the approach that I will follow.

### 3.2.2 May 26 – June 26

#### Week 1
Rewrite the entire "Brasil Participativo" home page, including the login going to the administration panel access part, complying with good boilerplate development practices.

#### Week 2
Work in the administration panel, understanding how information feeding of the participatory process, assembly, initiatives and conferences works, to transform these processes into customizable templates, where it is possible to select which functions to add or not, when creating a new participatory process model, optimizing the use of the platform and making it more dynamic and accessible.

#### Week 3
Continue the focus on transforming the remaining functions such as consultations, global moderators, newsletters and pages, taking into account whether or not they can be used by the institution, facilitating customization.

#### Week 4
Use the last week to take care of testing and final revisions before delivering the first version.

### 3.2.3 June 27 – July 12 
Finalize and submit project for mid-term evaluation.

## 3.2.4 July 13 – August 16 
Work on changes and improvements requested after mid-term evaluation and prepare documentation for hand off.

## 3.2.5 August 17 – August 26 
Final review and code submit.

## 3.2.6 September 17 
Final results announcement.

# 4 About Me

My name is Samara Alves Quintino, I'm an undergraduate student pursuing a Bachelor's degree on System Analisys and Development at University Estácio de Sá, currently on 4º semester, and this is my first time applying to Google Summer of Code.

I currently work in a part time job as a development analyst, my career in technology is recent having started just 2 years ago. I have experience in some programming languages ​​such as Delphi which I use at work, Python in personal projects and some databases such as Oracle and Postgres.

I am a mother of two children and I actively participate in the PyLadies Goiânia community, as a way to find encouragement and motivation in addition to helping other women find themselves in technology.

 I saw GSOC as a great opportunity for growth and learning. Since choosing to follow the back end path, I have always had a clear idea that I wanted to contribute to open source, and I am sure that I will be able to fulfill the proposed demands.

Contact points and general information :

Timezone : UTC-3
Primary language : Brazilian Portuguese
Other languages : English (Professional Proficiency)
E-mail : sam.blacklotus@gmail.com
Postal address: Anápolis, Goiás, Brazil


