# Football-match-analysis-sql-data-warehouse
Football Match Analysis Data Warehouse using Star Schema Design. Includes player performance analytics, team statistics, and stadium insights.

**Project Title**: Match Analysis  
**Level**: Intermediate  
**Database**: `match_analysis` 

![image](https://user-images.githubusercontent.com/56026296/229609893-b7b1f261-5941-45af-8322-1ccb2535d36b.png)


## Analysis Included
1.Team Performance Analysis   
2.Playmaker Analysis   
3.Possession Strategy Analysis   
4.Stadium Impact Analysis   
5.Creative Players Performance   
6.Venue-Based Player Performance   
7.Goal Efficiency Analysis   
8.Seasonal Performance Insight   
9.Player Contribution Analysis   


## Project Overview
Star Schema football analytics database built using MySQL.
Analyzes player performance, team stats, and stadium insights.

### Creating Tables
```sql
create schema match_analysis;
use match_analysis;

CREATE TABLE Player_Dim (
    Player_ID INT PRIMARY KEY,
    Player_Name VARCHAR(50),
    Position VARCHAR(20),
    Age INT,
    Nationality VARCHAR(30)
);

CREATE TABLE Team_Dim (
    Team_ID INT PRIMARY KEY,
    Team_Name VARCHAR(50),
    Coach VARCHAR(50),
    City VARCHAR(50)
);

CREATE TABLE Date_Dim (
    Date_ID INT PRIMARY KEY,
    Match_Date DATE,
    Day INT,
    Month INT,
    Year INT
);

CREATE TABLE Stadium_Dim (
    Stadium_ID INT PRIMARY KEY,
    Stadium_Name VARCHAR(50),
    City VARCHAR(50),
    Capacity INT
);

CREATE TABLE Match_Fact (
    Match_ID INT PRIMARY KEY,
    Player_ID INT,
    Team_ID INT,
    Date_ID INT,
    Stadium_ID INT,
    Goals INT,
    Assists INT,
    Passes INT,
    Possession DECIMAL(5,2),
    FOREIGN KEY (Player_ID) REFERENCES Player_Dim(Player_ID),
    FOREIGN KEY (Team_ID) REFERENCES Team_Dim(Team_ID),
    FOREIGN KEY (Date_ID) REFERENCES Date_Dim(Date_ID),
    FOREIGN KEY (Stadium_ID) REFERENCES Stadium_Dim(Stadium_ID)
);
```
### Inserting Values
```sql
INSERT INTO Player_Dim VALUES
(1, 'Arjun Mehta', 'Striker', 24, 'India'),
(2, 'Sahil Raina', 'Midfielder', 27, 'India'),
(3, 'Rahul Kapoor', 'Defender', 29, 'India'),
(4, 'Vikram Singh', 'Goalkeeper', 25, 'India'),
(5, 'Amit Joshi', 'Striker', 23, 'India'),
(6, 'Manish Yadav', 'Midfielder', 28, 'India'),
(7, 'Kunal Sharma', 'Defender', 26, 'India'),
(8, 'Rohit Verma', 'Striker', 24, 'India'),
(9, 'Deepak Nair', 'Midfielder', 27, 'India'),
(10, 'Ankit Chauhan', 'Defender', 25, 'India'),
(11, 'Sumit Shah', 'Defender', 24, 'India'),
(12, 'Aniket Sharma', 'Goalkeeper', 30, 'India'),
(13, 'Vikram Patil', 'Striker', 23, 'India'),
(14, 'Manish Kulkarni', 'Midfielder', 25, 'India'),
(15, 'Ajay Menon', 'Defender', 27, 'India'),
(16, 'Praveen Nair', 'Midfielder', 29, 'India'),
(17, 'Saurabh Gupta', 'Striker', 24, 'India'),
(18, 'Rohit Verma', 'Defender', 26, 'India'),
(19, 'Deepak Chauhan', 'Goalkeeper', 31, 'India'),
(20, 'Naveen Shetty', 'Midfielder', 25, 'India'),
(21, 'Akash Yadav', 'Striker', 22, 'India'),
(22, 'Harish Bansal', 'Defender', 28, 'India'),
(23, 'Siddharth Iyer', 'Midfielder', 27, 'India'),
(24, 'Vishal Singh', 'Striker', 24, 'India'),
(25, 'Sameer Khan', 'Goalkeeper', 29, 'India'),
(26, 'Pankaj Sharma', 'Defender', 30, 'India'),
(27, 'Amit Desai', 'Midfielder', 23, 'India'),
(28, 'Lokesh Joshi', 'Striker', 25, 'India'),
(29, 'Yash Mehra', 'Defender', 27, 'India'),
(30, 'Ashutosh Pandey', 'Midfielder', 26, 'India'),
(31, 'Mohit Sinha', 'Goalkeeper', 28, 'India'),
(32, 'Ravindra Pawar', 'Striker', 24, 'India'),
(33, 'Abhishek Choudhary', 'Midfielder', 25, 'India'),
(34, 'Chirag Jain', 'Defender', 29, 'India'),
(35, 'Tejas Rane', 'Striker', 22, 'India'),
(36, 'Suresh Pillai', 'Midfielder', 30, 'India'),
(37, 'Arvind Kapoor', 'Goalkeeper', 31, 'India'),
(38, 'Vinay Kumar', 'Defender', 26, 'India'),
(39, 'Kunal Thakur', 'Striker', 25, 'India'),
(40, 'Gaurav Bhatia', 'Midfielder', 27, 'India'),
(41, 'Anil Dutta', 'Defender', 29, 'India'),
(42, 'Shivam Pathak', 'Goalkeeper', 30, 'India'),
(43, 'Devendra Saxena', 'Striker', 24, 'India'),
(44, 'Harshit Agarwal', 'Midfielder', 28, 'India'),
(45, 'Krishnan Menon', 'Defender', 27, 'India'),
(46, 'Omkar Kulkarni', 'Striker', 25, 'India'),
(47, 'Rajesh Joshi', 'Midfielder', 26, 'India'),
(48, 'Suraj Patil', 'Goalkeeper', 30, 'India'),
(49, 'Nikhil Saxena', 'Defender', 29, 'India'),
(50, 'Ayaan Khan', 'Striker', 23, 'India'),
(51, 'Pritam Roy', 'Midfielder', 25, 'India'),
(52, 'Sandeep Rathore', 'Defender', 27, 'India'),
(53, 'Vikas Sharma', 'Goalkeeper', 31, 'India'),
(54, 'Rohan Kapoor', 'Striker', 24, 'India'),
(55, 'Dev Patel', 'Midfielder', 26, 'India'),
(56, 'Kishore Naik', 'Defender', 28, 'India'),
(57, 'Mohan Lal', 'Goalkeeper', 30, 'India'),
(58, 'Jatin Arora', 'Striker', 25, 'India'),
(59, 'Parth Bansal', 'Midfielder', 29, 'India'),
(60, 'Uday Chouhan', 'Defender', 27, 'India'),
(61, 'Shyam Sundar', 'Goalkeeper', 30, 'India'),
(62, 'Manoj Yadav', 'Striker', 23, 'India'),
(63, 'Farhan Sheikh', 'Midfielder', 25, 'India'),
(64, 'Kapil Dev', 'Defender', 28, 'India'),
(65, 'Prashant Saini', 'Goalkeeper', 29, 'India'),
(66, 'Bhavesh Rathod', 'Striker', 24, 'India'),
(67, 'Chandan Kumar', 'Midfielder', 26, 'India'),
(68, 'Lalit Chauhan', 'Defender', 30, 'India'),
(69, 'Akhil Joshi', 'Goalkeeper', 31, 'India'),
(70, 'Sanjay Malhotra', 'Striker', 25, 'India'),
(71, 'Dhruv Sharma', 'Midfielder', 27, 'India'),
(72, 'Aditya Prasad', 'Defender', 29, 'India'),
(73, 'Tushar Verma', 'Goalkeeper', 30, 'India'),
(74, 'Deependra Singh', 'Striker', 24, 'India'),
(75, 'Shivraj Chauhan', 'Midfielder', 26, 'India'),
(76, 'Rajiv Kapoor', 'Defender', 28, 'India'),
(77, 'Harendra Kumar', 'Goalkeeper', 31, 'India'),
(78, 'Rakesh Patil', 'Striker', 23, 'India'),
(79, 'Tarun Ghosh', 'Midfielder', 25, 'India'),
(80, 'Mayank Bhatt', 'Defender', 27, 'India'),
(81, 'Anoop Choudhary', 'Goalkeeper', 30, 'India'),
(82, 'Laxman Meena', 'Striker', 24, 'India'),
(83, 'Sohail Khan', 'Midfielder', 26, 'India'),
(84, 'Karthik Iyer', 'Defender', 29, 'India'),
(85, 'Girish Kumar', 'Goalkeeper', 28, 'India'),
(86, 'Ravi Joshi', 'Striker', 25, 'India'),
(87, 'Narendra Sahu', 'Midfielder', 27, 'India'),
(88, 'Balaji Menon', 'Defender', 30, 'India'),
(89, 'Ashwin Deshmukh', 'Goalkeeper', 31, 'India'),
(90, 'Hemant Chauhan', 'Striker', 24, 'India'),
(91, 'Pavan Kumar', 'Midfielder', 26, 'India'),
(92, 'Varun Agarwal', 'Defender', 28, 'India'),
(93, 'Sudarshan Pillai', 'Goalkeeper', 30, 'India'),
(94, 'Raghav Sharma', 'Striker', 25, 'India'),
(95, 'Prem Singh', 'Midfielder', 27, 'India'),
(96, 'Yogesh Desai', 'Defender', 29, 'India'),
(97, 'Sachin Thakur', 'Goalkeeper', 31, 'India'),
(98, 'Anant Patil', 'Striker', 24, 'India'),
(99, 'Virat Sharma', 'Midfielder', 26, 'India'),
(100, 'Neel Kapoor', 'Defender', 28, 'India');


INSERT INTO Team_Dim VALUES
(101, 'Ruston United', 'Ravi Kumar', 'Bangalore'),
(102, 'Mumbai FC', 'Sunil Sharma', 'Mumbai'),
(103, 'Delhi Dynamos', 'Anil Kapoor', 'Delhi'),
(104, 'Chennai Warriors', 'Praveen Iyer', 'Chennai'),
(105,'Pune Supergiants','Mahesh Ghantenavar','Pune'),
(106,'Mohan Bagun','Sandesh Jhingan','Kolkata'),
(107,'Northeast United','Dhananjay Oinam','Nagaland'),
(108,'FC Goa','Amey Deshpande','Goa'),
(109,'Noida Superstar','Vedant Kulkarni','Noida'),
(110,'Talegaon Strikers','Aditya Kalbhor','Lonavala');
select * from team_dim;

UPDATE team_dim
SET coach = LTRIM(coach)
WHERE coach = ' Amey Deshpande';

INSERT INTO Stadium_Dim VALUES
(501, 'Kanteerava Stadium', 'Bangalore', 25000),
(502, 'Cooperage Ground', 'Mumbai', 15000),
(503, 'Jawaharlal Nehru Stadium', 'Delhi', 60000),
(504, 'Marina Arena', 'Chennai', 35000),
(505, 'Allianz Arena', 'Lonavala', 65000),
(506, 'MCA Arena', 'Pune', 55000);

INSERT INTO Stadium_Dim VALUES
(500, 'Wankhede Arena', 'Navi Mumbai', 53000);

INSERT INTO Date_Dim VALUES
(20250701, '2025-07-01', 1, 7, 2025),
(20250702, '2025-07-02', 2, 7, 2025),
(20250703, '2025-07-03', 3, 7, 2025),
(20250704, '2025-07-04', 4, 7, 2025),
(20250705, '2025-07-05', 5, 7, 2025),
(20250706, '2025-07-06', 6, 7, 2025),
(20250707, '2025-07-07', 7, 7, 2025),
(20250708, '2025-07-08', 8, 7, 2025),
(20250709, '2025-07-09', 9, 7, 2025),
(20250710, '2025-07-10', 10, 7, 2025),
(20250711, '2025-07-11', 11, 7, 2025),
(20250712, '2025-07-12', 12, 7, 2025),
(20250713, '2025-07-13', 13, 7, 2025),
(20250714, '2025-07-14', 14, 7, 2025),
(20250715, '2025-07-15', 15, 7, 2025),
(20250716, '2025-07-16', 16, 7, 2025),
(20250717, '2025-07-17', 17, 7, 2025),
(20250718, '2025-07-18', 18, 7, 2025),
(20250719, '2025-07-19', 19, 7, 2025),
(20250720, '2025-07-20', 20, 7, 2025),
(20250721, '2025-07-21', 21, 7, 2025), 
(20250722, '2025-07-22', 22, 7, 2025),
(20250723, '2025-07-23', 23, 7, 2025),
(20250724, '2025-07-24', 24, 7, 2025),
(20250725, '2025-07-25', 25, 7, 2025),
(20250726, '2025-07-26', 26, 7, 2025),
(20250727, '2025-07-27', 27, 7, 2025),
(20250728, '2025-07-28', 28, 7, 2025),
(20250729, '2025-07-29', 29, 7, 2025),
(20250730, '2025-07-30', 30, 7, 2025),
(20250731, '2025-07-31', 31, 7, 2025);
```

### 1️.Team Performance Analysis:
How many total goals were scored by each team during the 2025 season?

```sql
SELECT 
    t.Team_Name, SUM(m.Goals) AS Total_Goals
FROM
    Match_Fact m
        JOIN
    Team_Dim t ON m.Team_ID = t.Team_ID
        JOIN
    Date_Dim d ON m.Date_ID = d.Date_ID
WHERE
    d.Year = 2025
GROUP BY t.Team_Name
ORDER BY Total_Goals DESC;
```

### 2. Playmaker Analysis

Which players ranked in the top 5 for total assists across all matches?

```sql
SELECT 
    p.Player_Name, SUM(m.Assists) AS Total_Assists
FROM
    Match_Fact m
        JOIN
    Player_Dim p ON m.Player_ID = p.Player_ID
GROUP BY p.Player_Name
ORDER BY Total_Assists DESC
LIMIT 5;
```

### 3.Possession Strategy Analysis

What was the average ball possession percentage achieved by each team?
```sql
SELECT 
    t.Team_Name, ROUND(AVG(m.Possession), 2) AS Avg_Possession
FROM
    Match_Fact m
        JOIN
    Team_Dim t ON m.Team_ID = t.Team_ID
GROUP BY t.Team_Name;
```

### 4.Stadium Impact Analysis

Which stadiums recorded the highest number of goals scored?
```sql
SELECT 
    s.Stadium_Name, SUM(m.Goals) AS Goals_Scored
FROM
    Match_Fact m
        JOIN
    Stadium_Dim s ON m.Stadium_ID = s.Stadium_ID
GROUP BY s.Stadium_Name
ORDER BY Goals_Scored DESC;
```

### 5. Creative Players Performance

Who were the top 5 assist providers based on overall match performance?
```sql
SELECT 
    p.Player_Name, SUM(f.Assists) AS Total_Assists
FROM
    Match_Fact f
        JOIN
    Player_Dim p ON f.Player_ID = p.Player_ID
GROUP BY p.Player_Name
ORDER BY Total_Assists DESC
LIMIT 5;
```

### 6.Venue-Based Player Performance

How did player goal contributions vary across different stadiums?
```sql
SELECT 
    p.Player_Name, s.Stadium_Name, SUM(f.Goals) AS Goals
FROM
    Match_Fact f
        JOIN
    Player_Dim p ON f.Player_ID = p.Player_ID
        JOIN
    Stadium_Dim s ON f.Stadium_ID = s.Stadium_ID
GROUP BY p.Player_Name , s.Stadium_Name
ORDER BY Goals DESC;
```

### 7. Goal Efficiency Analysis

Which players demonstrated the highest goals-per-match efficiency?
```sql
SELECT 
    p.Player_Name,
    COUNT(DISTINCT f.Match_ID) AS Matches_Played,
    SUM(f.Goals) AS Total_Goals,
    ROUND(SUM(f.Goals) / COUNT(DISTINCT f.Match_ID),
            2) AS Goals_Per_Match
FROM
    Match_Fact f
        JOIN
    Player_Dim p ON f.Player_ID = p.Player_ID
GROUP BY p.Player_Name
ORDER BY Goals_Per_Match DESC;
```

### 8.Seasonal Performance Insight

During which month did a specific player achieve peak goal-scoring performance?
```sql
SELECT 
    p.Player_Name, d.Month, SUM(f.Goals) AS Goals
FROM
    Match_Fact f
        JOIN
    Player_Dim p ON f.Player_ID = p.Player_ID
        JOIN
    Date_Dim d ON f.Date_ID = d.Date_ID
WHERE
    p.Player_Name = 'Arjun Mehta'
GROUP BY p.Player_Name , d.Month
ORDER BY Goals DESC
LIMIT 1;
```

### 9. Player Contribution Analysis:
Which players contributed the most to total goal involvements (Goals + Assists) ?

```sql
SELECT 
    p.Player_Name,
    SUM(f.Goals) AS Total_Goals,
    SUM(f.Assists) AS Total_Assists,
    SUM(f.Goals + f.Assists) AS Total_Goal_Involvements
FROM
    Match_Fact f
        JOIN
    Player_Dim p ON f.Player_ID = p.Player_ID
GROUP BY p.Player_Name
ORDER BY Total_Goal_Involvements DESC;
```
