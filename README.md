# Assignment 1 — Simulated Annealing: Exam Timetable Scheduling
## Observation Report

Student Name  : Palugulla Poojitha  
Student ID    : 2310040039
Date Submitted: 26-03-2026  

---

## How to Submit

1. Run each experiment following the instructions below
2. Fill in every answer box — do not leave placeholders
3. Make sure the plots/ folder contains all required images
4. Commit this README and the plots/ folder to your GitHub repo

---

## Before You Begin — Read the Code

Open sa_timetable.py and read through it. Then answer these questions.

Q1. What does `count_clashes()` measure? What value means a perfect timetable?

[ count_clashes() measures the number of conflicts in the timetable, i.e., how many exams are scheduled in the same time slot for students who have overlapping subjects.

A perfect timetable has 0 clashes, meaning no student has two exams at the same time. ]

Q2. What does `generate_neighbor()` do? How is the new timetable different from the current one?

[generate_neighbor() creates a new timetable by making a small change to the current one, usually by moving a subject to a different time slot.

This produces a slightly different timetable that can either improve or worsen the number of clashes, helping the algorithm explore possible solutions.]

Q3. In `run_sa()`, there is this line:
if delta < 0 or random.random() < math.exp(-delta / T):
What does this line decide? Why does SA sometimes accept a worse solution?

[This line decides whether to accept the new solution. If the new solution is better (delta < 0), it is always accepted. If it is worse, it may still be accepted with a certain probability.

Simulated Annealing accepts worse solutions to avoid getting stuck in local minima and to explore more possible solutions, especially at higher temperatures.]

---

## Experiment 1 — Baseline Run

Instructions: Run the program without changing anything.
python sa_timetable.py

Fill in this table:

| Metric | Your result |
|--------|-------------|
| Number of iterations completed |1379 |
| Clashes at iteration 1 |12 |
| Final best clashes |3 |
| Did SA reach 0 clashes? (Yes / No) |No |

Copy the printed timetable output here:
[ Final Timetable
------------------------------------------
  Slot 1:  Geography
  Slot 2:  Chemistry, English
  Slot 3:  History, Computer Science, Economics
  Slot 4:  Biology, Statistics
  Slot 5:  Mathematics, Physics
------------------------------------------
  Total clashes : 3]

Look at `plots/experiment_1.png` and describe what you see (2–3 sentences).  
*Where does the biggest drop in clashes happen? Does the curve flatten out?*
[ The plot shows a sharp decrease in clashes during the initial iterations, indicating rapid improvement at the beginning. 

After that, the curve gradually flattens, showing that the algorithm stabilizes and makes only small improvements as it approaches a near-optimal solution.]

---

## Experiment 2 — Effect of Cooling Rate

Instructions: In sa_timetable.py, find the # EXPERIMENT 2 block in __main__.  
Copy it three times and run with cooling_rate = 0.80, 0.95, and 0.995.  
Save plots as experiment_2a.png, experiment_2b.png, experiment_2c.png.

Results table:

| cooling_rate | Final clashes | Iterations completed | Reached 0 clashes? |
|-------------|---------------|----------------------|--------------------|
| 0.80        |     8         |        31            |       No           |
| 0.95        |     3         |        135           |       No           |
| 0.995       |     3         |        1379          |       No           |
Compare the three plots. What do you notice about how fast vs slow cooling affects the result? (3–4 sentences)  
*Hint: Fast cooling = temperature drops quickly. Does it have time to explore well?*
[When the cooling rate is too low (0.80), the temperature drops quickly, so the algorithm stops exploring early and gets stuck in a poor solution with more clashes.

With a moderate cooling rate (0.95), the algorithm performs better, allowing some exploration and reaching fewer clashes.

With a very slow cooling rate (0.995), the algorithm explores more thoroughly and consistently finds a better solution, although it takes more iterations. This provides a balance between exploration and convergence. ]

Which cooling_rate gave the best result? Why do you think that is?
[The best result was obtained with cooling_rate = 0.995.

This is because slower cooling allows the algorithm more time to explore different solutions and escape local minima, leading to a better final timetable with fewer clashes. ]

---

## Summary

Complete this table with your best result from each experiment:

| Experiment | Key setting | Final clashes | Main finding in one sentence |
|------------|-------------|---------------|------------------------------|
| 1 — Baseline | cooling_rate = 0.995 |3 |The algorithm reduces clashes quickly and stabilizes near an optimal solution. |
| 2 — Cooling rate | cooling_rate = ___ |3 |Slower cooling produces better solutions by allowing more exploration. |

In your own words — what is the most important thing you learned about Simulated Annealing from these experiments? (3–5 sentences)
[From these experiments, I learned that Simulated Annealing is a powerful optimization technique that balances exploration and exploitation. The temperature parameter plays a crucial role in determining how the algorithm searches for solutions. 

If the temperature decreases too quickly, the algorithm may get stuck in poor solutions, while slower cooling allows it to explore more possibilities and find better solutions. 

Accepting worse solutions initially helps avoid local minima, which is a key advantage over greedy algorithms. Overall, parameter tuning is very important for achieving the best performance in Simulated Annealing.]

---

## Submission Checklist

- [ ] Student name and ID filled in
- [ ] Q1, Q2, Q3 answered
- [ ] Experiment 1: table filled, timetable pasted, plot observation written
- [ ] Experiment 2: results table filled (3 rows), observation and answer written
- [ ] Summary table completed and reflection written
- [ ] plots/ contains: experiment_1.png, experiment_2a.png, experiment_2b.png, experiment_2c.png