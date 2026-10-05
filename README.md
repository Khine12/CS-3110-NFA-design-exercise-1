# NFA Design — CS 3110.03

Problems chosen: #7, #9, #11, #23, #24 (from the N/DFA/RE design list)

See `n07r.md`, `n09r.md`, `n11r.md`, `n23r.md`, `n24r.md` for each problem's NFA design, diagram, and test results.

## Reflection

1. **Which problem(s) gave you the most trouble? Did you avoid any problem that was too challenging to finish by the deadline? Did you ask questions to AI/instructor?**

   Problem 23 was the trickiest one to reason about by hand. It's the union of "odd length" and the exact string "01", so I used an ε-transition from the start state to split into two branches. When tracing it on paper I had to keep track of both branches at the same time, and it was easy to forget that the "01" branch is still alive after the first symbol even though the parity branch has already moved on. I didn't skip any problems. I worked through the NFA designs and debugging with Claude (AI assistance). It helped me reason through the nondeterministic-guessing and ε-branching techniques, and I caught a real test-file mix-up on problem 23 by re-verifying results myself rather than trusting the first batch run. I didn't ask the instructor directly, but would reach out if I got stuck on a technique Claude couldn't clarify.

2. **Which problem(s) surprised you with a "gold-string"? Which next state(s) did you not account for in the subset of next states? Why? How will you make sure you avoid such errors in future flight/traffic/compiler state controller tasks, or in the course projects/exams?**

   My "gold-string" moment on Problem 23 turned out not to be a missing next state. It was my own mistake. I loaded `n07t.txt` instead of `n23t.txt` for the batch run, so "0110" came back rejected and I thought the NFA was broken. Once I reloaded the right file, all the results matched what I expected. The real lesson is to double-check which test file is loaded before trusting a batch result, especially when I'm working on several similar NFAs back to back. From now on I'm going to check the filename JFLAP shows before I click "Run Inputs."

3. **Other insights/comments/questions for the grader/instructor.**

   After doing all five, I noticed they really came down to two techniques. For the suffix/infix/position problems (#7, #9, #11), the NFA nondeterministically "guesses" where the important part of the string starts, and wrong guesses just die off. For the OR-type languages (#23, #24), I used ε-branching to run two simpler machines in parallel. Once I saw that pattern, the later problems went a lot faster than the first one.
