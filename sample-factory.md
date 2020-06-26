# Sample Factory

- Today I learned about [Sample Factory](https://sites.google.com/view/sample-factory), an asynchronous implementation of Proximal Policy Optimization that enables massively accelerated RL training of non-trivial control problems (i.e. VizDoom) on a single 10-core cpu and GTX Ti 1080 gpu machine.
- The architecture of Sample Factory enables high throughput training by combining a GPU-based rollout sampler with "off-policy correction techniques". Makes you wonder what could be achieved with methods that are off-policy by design.
- There is of course a lot of work making existing learning methods more sample efficient. However, given a vast amount of data, we can often train agents that are quite capable of doing the task for which they are designed, sometimes at superhuman levels.
- While one approach is obviously to throw tons of computers at the problem, the resources available on a relatively inexpensive research machine could be utilized a lot more effectively, and that's what this project aims to achieve.
- One of the big bottlenecks to optimal resource utilization in policy gradient learning is the policy update step, in which sampling must halt while experience is gathered and the policy trained via backpropagation. This was at least partially addressed, first on the CPU using multi-process experience collection in A3C and a GPU accelerated version, GA3C. IMPALA achieves further improvements, reporting a training frame rate of 24K FPS on a single 48-core machine and up to 250K FPS on a cluster with 500 CPUs, which..I guess the 500 CPUs each have much lower number of cores? Anyway...
- Note on Off-Policy RL: while Q-learning-style algorithms with their off-policy sampling are certainly very scalable, there are some theoretical and currently practical limitations on the kind of action spaces the Q-function can map to ([Vinyals, et al](https://www.nature.com/articles/s41586-019-1724-z)).


