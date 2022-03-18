# XZANDrive

## Overview

A File sharing server that is like GoogleDrive but can be hosted locally with minimal configuration.

## Use Case

Lately, I've been copying a lot of files through my local network and have been making use of the SMB protocol to transfer files. Downside is that it's a bit slow comparing to FTP which is much faster and reliable. In addition to that It can be hosted without any access cofiguration when a new machine is enters the network.

Another use case is when one is outside without a portable harddrive to copy files. This server can be hosted on a phone making use of Its storage and hosting it over hotspot, or a public Wifi.

<hr>

## Tech Stack Choices

### 1) NodeJS

I wanted to learn Backend using JS and such an idea is a great project for it because of the built-in asynchoronous functionality NodeJS provides.

### 2) SQLite3

For the project to be flexible and portable, a single file database is the best for such cause instead of deploying a seperate database server on each machine. In addition to that the database will only be used to store the app configuration like: User accounts, Shared folders directories, and User activity. (What's planned for now)

### 3) ExpressJS

For the backend, learning a non-battery framework is a great addition to my skill set where I can explore deeper on how a user session is established, how connections with a database occurs, and how to handle server requests with more flexibility.

### 4) ReactJS

I want to learn the most out of this project and for a responsive frontend and learning another framework that is widely used in industry will be a good addition to my skill set.

> Disclamer: I haven't uploaded any files of this project yet. Will do when its in a semi-ready stage.

<hr>

## Workflow

graph TD
    Endpoint["/"] --> LoggedIn{Is logged in?} -->|No| LogIn
    LogIn --> LoggedIn -->|Yes| Shared_Files_Endpoint
    Shared_Files_Endpoint -->|Get_Request| Database[(Database)]
    Database -->|Shared_Directories| Shared_Files_Endpoint

    Admin["/admin/"] --> Is_Admin{Is user an admin} -->|No| Shared_Files_Endpoint
    Is_Admin -->|Yes| Admin_Page -->|Get_Request| Database
    Database -->|Users Records<br>Shared Directories<br>Activity Log| Admin_Page

<hr>

## Future Implementations

> These may take place after finishing the primary infrastructure of the file sharing mechanism.

* Light-Dark Theme.
* Drag and Drop feature to quickly upload files.
* Adding custom editors to the app. DOCX-ODF editors, Markdown renderer, Code Highligters, ..etc.
* Implementing JWT Authentication.
* Implementing Video/Audio players.

<hr>

## Downsides

>	Still researching about how to overcome these weak points.

* Spamming can occur on login pages.
* Different networks require different IP configuration.

<hr>

## How I am learning this stack

1) NodeJS

I began to familarize myself with JS syntax and ECMAScript 6 features from thenewboston Youtube channel and began practising/tinkering with its functionalities. I also read a part of the documentation to get a clearer understanding of the asynchoronous functionality. Currently, I'm participating in **GSSoC'22** OpenSource contest, and most of my contributions are built using JS.

2) ExpressJS

Basics were also learnt from thenewboston, and continued building myself up using the documentation. (Currently, I'm studing how to establish an authenticated user session)

3) SQLite3

Since Express is a non-battery framework, I went ahead and learnt how to write SQL queries from a Udemy course and continued reading more documentations about connecting to a sqlite DB file using JS.

> I'm still working my way from here and going to add more updates as I learn more.

<hr>