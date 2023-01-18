## PROBLEM 1 (Top Competitors)

Julia just finished conducting a coding contest, and she needs your help assembling the leaderboard! Write a query to print the respective hacker_id and name of hackers who achieved full scores for more than one challenge. Order your output in descending order by the total number of challenges in which the hacker earned a full score. If more than one hacker received full scores in same number of challenges, then sort them by ascending hacker_id.
 
Input Format

The following tables contain contest data:
 
•	Hackers: The hacker_id is the id of the hacker, and name is the name of the hacker.  
•	Difficulty: The difficult_level is the level of difficulty of the challenge, and score is the score of the challenge for the difficulty level. 
•	Challenges: The challenge_id is the id of the challenge, the hacker_id is the id of the hacker who created the challenge, and difficulty_level is the level of difficulty of the challenge. 
•	Submissions: The submission_id is the id of the submission, hacker_id is the id of the hacker who made the submission, challenge_id is the id of the challenge that the submission belongs to, and score is the score of the submission. 
 

#### SUBMISSION 1

SELECT hackers.hacker_id,

hackers.name
        
FROM hackers

INNER JOIN submissions ON submissions.hacker_id=hackers.hacker_id
    
INNER JOIN challenges ON challenges.challenge_id=submissions.challenge_id
    
RIGHT JOIN difficulty ON difficulty.difficulty_level=challenges.difficulty_level
    
WHERE submissions.score=difficulty.score

GROUP BY hackers.hacker_id, hackers.name

HAVING COUNT(submissions.challenge_id)>1

ORDER BY COUNT(submissions.challenge_id) DESC, hackers.hacker_id;



## PROBLEM 2 (Placements)

You are given three tables: Students, Friends and Packages. Students contains two columns: ID and Name. Friends contains two columns: ID and Friend_ID (ID of the ONLY best friend). Packages contains two columns: ID and Salary (offered salary in $ thousands per month).
 
Write a query to output the names of those students whose best friends got offered a higher salary than them. Names must be ordered by the salary amount offered to the best friends. It is guaranteed that no two students got same salary offer.

#### SUBMISSION 2

SELECT s.name
FROM students AS s
INNER JOIN packages AS p ON p.id=s.id
INNER JOIN friends AS f ON f.id=s.id
INNER JOIN packages AS pc ON pc.id=f.friend_id
WHERE pc.salary > p.salary
ORDER BY pc.salary;



## PROBLEM 3 

Harry Potter and his friends are at Ollivander's with Ron, finally replacing Charlie's old broken wand.
Hermione decides the best way to choose is by determining the minimum number of gold galleons needed to buy each non-evil wand of high power and age. Write a query to print the id, age, coins_needed, and power of the wands that Ron's interested in, sorted in order of descending power. If more than one wand has same power, sort the result in order of descending age.

Input Format

The following tables contain data on the wands in Ollivander's inventory:
•	Wands: The id is the id of the wand, code is the code of the wand, coins_needed is the total number of gold galleons needed to buy the wand, and power denotes the quality of the wand (the higher the power, the better the wand is).
 
•	Wands_Property: The code is the code of the wand, age is the age of the wand, and is_evil denotes whether the wand is good for the dark arts. If the value of is_evil is 0, it means that the wand is not evil. The mapping between code and age is one-one, meaning that if there are two pairs, (code1 and age1)  and (code2 and age2) , then code1≠code2 and age1≠age2.
 
#### SUBMISSION 3

SELECT wands.id,
       wands_property.age,
       wands.coins_needed,
       wands.power
FROM wands
INNER JOIN wands_property ON wands_property.code=wands.code
WHERE wands.coins_needed = (SELECT MIN(W.coins_needed)
                        FROM wands W INNER JOIN Wands_Property WP
                        ON W.code = WP.code
                        WHERE wands.power = W.power AND 
                        wands_property.age = WP.age AND WP.is_evil = 0)
ORDER BY wands.power DESC, wands_property.age DESC;
