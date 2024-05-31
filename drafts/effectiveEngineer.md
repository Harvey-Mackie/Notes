# Chapter 8 - Balance Quality with Pragmatism.
[Still to be refined]
- Software boils down to a matter of tradeoffs, there's no universal rule on how to do things.

Code reviews
	- Downside of strict code reviews/quality checks - The overhead associated with experimental code is extremely high
	- Overly dogmatic code reviews, standardisation, and test coverage can have diminishing returns and actually ends up reducing your effectiveness. 
	- The more recent the employee, the more be valuable the code reviews are as it helps them get up to/learn the team standards.
	- Code review benefits
		- Catching bugs or design shortcomings early
		- Increasing accountability for code 
		- Positive modeling of how to write good code (pattern match good code)
		- Share working knowledge of code base
		- Increase long-term agility (easier to change good code)
Abstractions
	- Abstraction can save time and increase effectiveness. Look at MapReduce, the implementation is complex but the abstraction is easy to use, you don't even need to know the core logic, just the output. The right abstraction can increase engineering productivity
		- Makes it easier to apply future improvements
		- Solves the hard problem once and the solution can be used thousands of times
- Building an abstraction comes with a trade off. It ends up create a more general solution. Also, it takes time, you need to make sure it's worth it. Also, if you make the abstraction too early, you risk incorrectly designing it.
- Get better by studying other peoples abstractions