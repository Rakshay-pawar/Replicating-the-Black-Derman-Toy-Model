# Replicating-the-Black-Derman-Toy-Model
We delve into the construction and utilization of the Black-Derman-Toy model to construct an interest rate tree, based on the provided volatility and term structure data. Using the created tree, we calculate the expected future interest rates and compare them with initial forward rates. Further, we explore the pricing of European and American style options on a two-year bond using this model.

Please go through the "questions asked" to understand what all I did in depth. A brief is given below As park of my Fixed income assignment I implemented the following steps:

First, I focused on replicating the Black-Derman-Toy example from our class session. I started by extracting the volatility data for 'r' from the first sheet of the provided spreadsheet, then obtained the term structure data, denoted as D(T), from the second sheet. The third sheet contained the BDT tree, which I also examined for my reference.

I knew I didn't need to replicate the exact numbers, given that numerical programs may output different results due to their inherent features and quirks. This understanding guided my approach in solving the problem, helping me avoid undue stress over achieving the same results.

To tackle this task, I decided to write a program. This program was designed to solve for the correct drift or 'r' at each date that matches the discount bond price. I could have built this tree in Excel using the solver algorithm, but that would have involved manually using the solver twenty times - a process that seemed a bit tedious.

Once I had constructed the tree, I moved on to compute the expected value of 'r' at time zero, with horizons stretching out to .50 years, 1.00 years, and so forth up to the last date on the tree. I plotted a graph of the expected 'r' value against each horizon, which effectively illustrated these future rates. I then compared these expected future rates with the forward rates calculated from the initial term structure data.

Next, using the constructed tree, I computed the price of a five-year European call option on a two-year bond with a coupon rate of 4% and a strike price of 98. For this calculation, I needed to compute the price of the bond in five years at each of the 11 nodes in the tree. The bond price at any node was calculated using the D(0.5), D(1.0), D(1.5), and D(2.0) values applicable to that particular node and time.

I computed the D(T) values for each node by present valuing a cash flow of $1 received at different times back to time 5. With these values, I could then compute the value of the two-year bond at the expiration date of the call option at each node and compare it with the strike price. I followed this process for all the 11 nodes in the tree at five years. The call option value was then found by present valuing the option payoff from each node, all the way back to time zero.
