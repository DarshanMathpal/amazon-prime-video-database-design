# 🎬 Amazon Prime Video Data Modeling & SQL Analysis

## 📊 ER Diagram
![ER Diagram](https://github.com/user-attachments/assets/f5fd983e-80ac-4971-b283-783b4d8558a9)

## Overview
This project presents a real-world relational database design and analysis for Amazon Prime Video.  
It focuses on structuring data for users, content, and interactions to support scalable streaming and personalized recommendations.

---

## 📖 Quick Access

**View Full Project (Detailed Analysis + SQL Schema + ER Diagram)**: [Google Doc](https://docs.google.com/document/d/109l5h6BXwl0ozaDJFpL_o72UDI4DTi48/edit?usp=sharing) ⭐

---

## Project Details
- **Author**: Darshan Mathpal  
- **Type**: Database Design Project 
- **Domain**: Database Design / Data Engineering  

---

## 🛠️ Tech Stack

- **Database**: PostgreSQL  
- **Language**: SQL  
- **Concepts**: Relational Modeling, Database Normalization, ER Diagram Design, Data Integrity (Constraints & Keys)  

---

## 🚀 Key Highlights

- Designed a **relational database schema** for a real-world OTT platform  
- Modeled **user profiles, watch history, and ratings system**  
- Structured data to support **personalized recommendations**  
- Applied **real-world system design and normalization concepts**  
- Ensures **scalable and efficient data management for large user bases**  

---

## 🌍 Problem Statement

This project focuses on solving key challenges in modern streaming platforms:

- Limited access to on-demand entertainment  
- Difficulty in discovering relevant content  
- Lack of personalized user experience  

---

## 💡 Solution Approach

- Built a structured **relational database model**  
- Introduced **profile-based personalization**  
- Used **watch history + ratings** for recommendations  
- Organized content using **genre-based categorization**  

---

## 🧠 What This Project Demonstrates

- Database Design & Normalization  
- Real-World Product Thinking  
- User Behavior Modeling  
- SQL Schema Design  
- Scalable System Structuring  

---

## 📊 What's Inside the Project?

Detailed contents of the project include:

- Complete **Database Schema (SQL)**  
- Entity-Relationship (**ER Diagram**)  
- Real-world **case study analysis**  
- Feature-to-database mapping  
- Design rationale  

---

## 📊 Project Implementation

### 🧱 Database Schema

```sql
CREATE TABLE Users (
    user_id SERIAL PRIMARY KEY,
    email VARCHAR(100) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE Profiles (
    profile_id SERIAL PRIMARY KEY,
    user_id INT NOT NULL,
    profile_name VARCHAR(100),
    age_group VARCHAR(50),
    FOREIGN KEY (user_id) REFERENCES Users(user_id)
);

CREATE TABLE Genres (
    genre_id SERIAL PRIMARY KEY,
    genre_name VARCHAR(100)
);

CREATE TABLE Content (
    content_id SERIAL PRIMARY KEY,
    title VARCHAR(200),
    content_type VARCHAR(50),
    release_year INT,
    genre_id INT,
    FOREIGN KEY (genre_id) REFERENCES Genres(genre_id)
);

CREATE TABLE Watch_History (
    history_id SERIAL PRIMARY KEY,
    profile_id INT NOT NULL,
    content_id INT NOT NULL,
    watched_at TIMESTAMP,
    FOREIGN KEY (profile_id) REFERENCES Profiles(profile_id),
    FOREIGN KEY (content_id) REFERENCES Content(content_id)
);

CREATE TABLE Ratings (
    rating_id SERIAL PRIMARY KEY,
    profile_id INT NOT NULL,
    content_id INT NOT NULL,
    rating INT CHECK (rating >= 1 AND rating <= 5),
    FOREIGN KEY (profile_id) REFERENCES Profiles(profile_id),
    FOREIGN KEY (content_id) REFERENCES Content(content_id)
);
```
---

## 📜 License
Available for educational purposes.

---

## 📧 Contact

- **GitHub**: [@DarshanMathpal](https://github.com/DarshanMathpal)  
- **Repository**: [amazon-prime-video-database-design](https://github.com/DarshanMathpal/amazon-prime-video-database-design)  
