# Journal

## Week 1 and 2
  Only a few attempts have been made in the foray of binary neural network structures. Among these, BinaryConnect (Courbariaux et al, 2015) was one of the first. 
  Those that followed improved on BinaryConnect's example in various ways, and resulted in: Binarized Neural Network (Courbariaux et al, 2016), XNOR-net (Rastegari et al, 2016) and DoReFa-net (Zhou et al, 2016).
  However, as far as I could gather, all these systems implemented a binarization of full precision weights instead of a purely binary system. 
  It is remarked in these papers that completely binary systems are subject to high noise, low accuracy, and inconsistent convergence. 
  I hope to find a way to evade these pitfalls.

## Week 3
  I've realized a number of issues with my initial idea, and have attempted to remedy them. 
  I have settled on an initial draft iteration of my program structure, in the form of an agent - environment split. 
  The agent is in the form of a single node, with three inputs and one output. It contains a flag and a policy as state, in the form of a bit and a char. 
  Nodes have access to two functions, resolve and update. Resolve returns the action the agent would take given a particular pair of inputs and a policy. Update changes the policy of the node based on the previous iteration's reward.
  Additional details can be found in [abstract structure](./samples/abstract_structure.md)

## Week 4
  Implementation has been difficult to find time for, and has proceeded slowly. It is highly wordy and kind of messy, but the general structure seems ok. 
  I don't know how to implement a single bit as a data type in c++. What should conceptually be as simple as "data Bit = 0 | 1" is proving difficult to grok. 
  On the other hand, the representation of policy is incredibly clean, compacting an entire truth table into a single char. Doing the proper bit shifts for resolve will be a challenge however.
  Code will be at [Agent](./Agent.md) once it is presentable. 

## Week 5
  Midterms have further limited my time. Implementation of Agent has begun but is still incomplete. It is the priority for completion; Environment will come ASAP. 
  I'm now officially behind schedule.

## Week 6
  Agent is still under construction. Draft 1 is thrown away in favor of a rewrite. Figuring out how to represent the small data types is proving confusing. Deciding between stl:bitset and bit fields is based on conversions between them and other types. Not sure how to represent a single digit of hex better than an unsigned int bit fielded to 4

## Week 7
  I've chosen bitset for its ease of conversion. In particular, it allows the use of a bitset as an index into another bitset by way of `to_ulong()`. Agent is in a complete and workable place for a variety of test code. 
  It is surprisingly short and clean, (ignoring the comments,) belying the messy iteration it took to develop.

## Week 8
  Environment version 1 framework is in place. I'm catching up on my schedule!. I skipped Week 7's research goal in favor of implemenation time. 
  I worry about the recursive implementation of resolvetree, due to the foreseen extreme scaling problem of the project. A non-recursive rewrite of resolvetree will come when it is determined to be a performance bottleneck later down the line. 

## Week 9
  In a petty attempt to avoid iterators, I mis-designed some parts of Environment. In order to be scalable, dynamic arrays are all but required. A refactor using std::vector is in order next. 
  On the other hand, Environment empirically converges for one- and three-node trees, even with the current update function! In order to test on larger examples, a fuller test-data structure will be required. 
  Test data should consist of up to 2^order samples in the format: {2^order bools/bits of input data, 1 bool/bit of correct answer}
  Is it possible to cut off the "top" of the tree to produce a result consisting of more than 1 bit?
