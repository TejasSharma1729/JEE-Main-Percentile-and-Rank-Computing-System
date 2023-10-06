# JEE-Main-Percentile-and-Rank-Computing-System

# Objective
This project targets the leading educational organizations in India which conduct competitive exams on national scale, modelled closely on the JEE Mains exam. The software computes percentile and rank for all the students participating in competitive exams such as JEE mains, JEE advanced, NEET etc. and is designed to be easily extensible to other competitive exams both at national level and beyond. Customizable tie breaker algorithm will enable us to adapt this software to the needs of any competitive exam. The software also handles generation of data to match the real world scale, thereby facilitating validation of the tie breaker algorithm and overall testability of the application before deployment.

# Background
JEE Mains is one of the most popular exams in India written by more than 1 million students each year. It is the gateway to admission in most engineering colleges including National Institute of Technology (NITs), Indian Institute of Information Technology (IIITs) etc. and serves as the eligibility criteria for appearing in JEE advanced for admission in various Indian Institute of Technology (IITs). Students are assessed in 3 subjects viz. Mathematics, Physics and Chemistry. Being a competitive exam, students are allocated All India Ranks (AIR). Recently, the exam conducting authority National Testing Agency(NTA) has come up with the scheme of assigning Percentiles before assigning AIR. Percentile is an indicator of the number of students whose performances are exceeded by the mentioned student. It is usually expressed as a percentage of total students. For example, if a student obtains 95th percentile, it means that in every group of 100 students, the said candidate’s score is better than 95 students, i.e. his score is in the top 5% of the candidates.__
The exam is conducted in 2 to 4 batches every year and each batch has between 4 to 8 sessions i.e. exam dates. A student has option to appear in any or all of the batches and is allotted one session (i.e. exam date and 1 particular exam paper) per batch by the NTA. For each session, percentiles are computed based on total marks (out of 300), Mathematics score, Physics score and Chemistry score separately. In case the student chooses to appear in multiple batches, the best of his percentiles computed for each batch (the sessions she appeared in) separately, becomes her overall percentile. Then on comparing total percentile, mathematics percentile, physics percentile and chemistry percentile, the final ranks are allotted. NTA used to apply date of birth as a last resort for tie breaker (the older candidate gets higher rank). That practice has been discontinued now and candidates with identical percentiles in all subjects get identical rank.__
For the purpose of this project, we intend to work with the premise of two batches, with 4 sessions in each batch.

# Requirements
## Functional Requirements
* The system should generate unique Id for each student
* The system should allow students to register for multiple batches
* The system should allot unique session in each batch that the student has registered for
* The percentile should be calculated up to 7 decimal places
* The rank should be absolute. If 2 candidates get AIR 97, we should skip AIR 98 and allot AIR 99 to the candidate with the next higher score
* The percentile should be computed for each session
* The best percentile of a student across all batches she has appeared for, should be used for ranking
* The system should support queries
## Non-Functional Requirements
* The system should support up to 1.5 million records
* The system should be portable
* The data should be persistent in a database such as MySQL

# Execution Environment
* Language: Python 3.8
* Database: MySQL 8.0.23
* IDE: Spyder (Anaconda)
* Platform: Mac OS (Monterey)

# Python Features used
In this project I have used the following features of Python and Python library
* **SQL Connector**: Allows the user to interface python and MySQL [11], and type all SQL commands through python along with python modifications. In this program, all the SQL commands are executed through python, not directly in MySQL.
* **YAML Convertor**: Names are stored separately in a YAML file. The program uses a random algorithm to generate a name (first name + last name) for each candidate.
* **getpass module**: Allows the user to securely enter a password without it being displayed on the screen.
* **Lists**: Stores data (usually 1 record at a time) temporarily before writing onto MySQL and temporarily before displaying in the query output.
* **Functions**: Allows us to perform repetitive tasks with a different input parameter (or identical tasks) without writing code multiple times over.
* **csv Module**: Allows the user to read and write from CSV files (text files, entities separated by commas or delimiters, in rows that resemble those in MS Excel). This program (print marksheets and query module) writes data onto CSV files for viewing results in bulk.
* **numpy Module**: Allows the user to perform specific math tasks such as the probability distribution i.e. likelihood of a student having a particular mark range (important in the case of random data generators).

# High level design
The Application is developed as a set of independent modules that will handle data entry, automatic test data generation, computation and output of results. There is also a query module for analytics.
## Program components
* **Generate Master Data**: This is responsible for generating the student master data that includes fields such as first name, last name, email address, mobile number etc. While it is possible to manually enter data, we recommend using our automatic test generator which uses Python’s random and numpy modules to generate randomly student records. I have tested the generation for 1.5 million students.
* **Generate Test Sessions Data**: This module can be used to register the students for the various test sessions and update the marks. Like the master data, we recommend using the automatic generator to obtain target sample quickly to test the program.
* **Compute Percentile and Rank**: This module uses the MySQL commands to compute the percentile and rank for all the students. Percentile is computed for each batch in the session separately. The best percentile across sessions for each student is considered for the final rank computation. The unique feature of this project is the ability to customize the tie-breaker algorithm.
* **Print Marksheets**: This module generates mark sheets for all the students and can be combined with notification module to email the score card to students.
* **Query Module**: I have provided basic queries to obtain the list of students based on range of rank, marks in individual subjects etc. This module can be enhanced for advanced analytics and fraud detection in future.












