---
description: Game Theory Analysis
---

# DPOS Borda Count

## Game Theory Analysis

### I. Preface:

Since Daniel Larimer introduced DPoS into EOS, how to better select Block Producers has become the focus of much community debate.

In this regard, BOS follows the EOS voting mechanism. That is a one-vote multi-selection \(maximum 30 selections\) mechanism. Due to the existence of Pareto's law, the voting rights tend to be concentrated in the hands of a few people. As well, a one-vote multi-selection mechanism allows token holders to trade votes, which ultimately leads to the Block Producers being controlled in the hands of a small number of token holders, thereby increasing the imbalance and centralization of the Block Producers, further leading to an increase in the gap between rankings. To this end, in the design of the BET voting system, we aim to introduce an improved [Borda voting mechanism](https://en.wikipedia.org/wiki/Borda_count) to alleviate this problem in order to find a more reasonable means to make a corresponding contribution in ensuring system security and widespread distribution; which ultimately leads to a better and more inclusive distribution of WPS funds.

### II. Proof of Stake mechanism and Voting:

1. There are many articles about the Proof of Stake mechanism. There is no more detailed discussion here. Only the discussion of Block Producer concentration and security is discussed. For the sake of discussion, we simplify the above. We assume that all voting rights are from voters, simplifying the original model as a probability discovery model, then we assume that a holder's shareholding ratio is Q, secret cheating function H, cheating is found after loss function F\(Q\), maintaining system stability. The general return function is X\(Q\), the cheating gain is W, the hypothetical function here is only used for qualitative analysis, so we can simply get the strategic relationship of the stakeholder:

Judging the relationship between W+\(H-1\)\*F\(Q\) and X\(Q\) and determining the corresponding strategy. Because F is a positive correlation function of Q, X is also a positive correlation function of Q, and W is a random parameter with speculation. So it can be concluded that the cheating gain will be significantly reduced with the increase of Q, under the assumption of rational natural person.

Choosing to maintain justice is a dominant strategy. So from this perspective, the PoS mechanism is a stable model. In fact, when we further analyze the ethical parameters, we can obtain the following relationships and conclusions between the equity structure and the stakeholders' income:

#### A\) Absolute concentration structure of Shares

If the equity is absolutely concentrated on the network operators, the supervision will be difficult, and the moral value of the network operators will decrease or even become negative.

Operator responsibility \(→min\)=operator morality \(→-\)×{1+ operator asset ownership \(max\)}

stakeholders' income \(→min\)=operator's responsibility \(→min\)×operator's ability×operating conditions.

#### B\) Relatively concentrated structure of equity

The relative concentration of equity can encourage operators, stabilize the backbone team, and generate checks and balances.

Operator Responsibility \(→max\)=Operator Ethics \(→max\)×{1+ Operator Asset Ownership \(max\)}

stakeholders' income \(→max\)=operator's responsibility \(→max\)×operator's ability×operating conditions.

#### C\) Equity dispersion structure

#### The equity is too scattered, the supervisory motivation is insufficient, and the moral value of the network operators will decrease or even become negative.

Operator Responsibility \(→min\)=Operator Ethics \(→-\)×{1+ Operator Asset Ownership \(min\)}

stakeholders' income \(→min\)=operator's responsibility \(→min\)×operator's ability×operating conditions.

From the analysis, we can determine that \(B\) relative concentration of equity is the preferred equity structure \(for detailed knowledge, please refer to the books and papers related to equity structure\).

Therefore, we need to avoid the concentration of large token holder consortiums under the premise of the stability of the system. So the question remains: is there an ideal voting solution?

### 2. Voting and election

Before discussing this issue in detail, let's try to define the problem:

We assume that there are N people participating in the election, there are a total of K people to vote, and there is an arrangement in the satisfaction of each voter in the hearts of the candidates. Our aim is to develop an election plan that will eventually be "fair" for everyone. The sequence of voting results.

So what is fair? Here we use the five rules of arrow:

* Every voter has the same influence; further, it is non-authoritarian.
* In addition to being unreasonable, voters have no other restrictions on the ordering of their minds.
* If all voters think A &gt; B, the election result will also show A &gt; B.
* The ranking of the election results for A and B should be determined only by the relative order of A and B within the file, regardless of any third party.
* If all voters are rationally sorting the choices and voting honestly, the results of the elections should also show a rational order.

But unfortunately there are a variety of proof methods to prove that such "justice" does not exist, which is also the content of the arrow impossible theorem. Since our system will be modified based on the Borda system, here we give proof of the theorem in the Borda case:

Let a given k integers m1, m2, ..., mk, let σ\(1,2,...,n\) be a permutation group of \(1,2,...,n\), and define the following mapping:

[![img](https://camo.githubusercontent.com/e3c80437c5f16f1d54920a53915ff59b06d227ef/68747470733a2f2f6c68362e676f6f676c6575736572636f6e74656e742e636f6d2f376578735668717750503779575769396c5770494b4f7948496552314d6c366e5a6b4e5563386b376436696d63353441495a63586c627238533243595676544c635a6c4e46582d53376a30566c6553425054767852674d4935634f6a4a684951425a6a5431494437524f6e714b78694c4544794f546766617a6b5378614448687263476a6d734855)](https://camo.githubusercontent.com/e3c80437c5f16f1d54920a53915ff59b06d227ef/68747470733a2f2f6c68362e676f6f676c6575736572636f6e74656e742e636f6d2f376578735668717750503779575769396c5770494b4f7948496552314d6c366e5a6b4e5563386b376436696d63353441495a63586c627238533243595676544c635a6c4e46582d53376a30566c6553425054767852674d4935634f6a4a684951425a6a5431494437524f6e714b78694c4544794f546766617a6b5378614448687263476a6d734855)

For any set of numbers t1&gt;t2&gt;...&gt;tn, use the above k permutations to make an n×k matrix:

[![img](https://camo.githubusercontent.com/d42aab902ae670955ed94cb7682dba66b7eca8b0/68747470733a2f2f6c68352e676f6f676c6575736572636f6e74656e742e636f6d2f58506444452d343862366a6f7770744b5968446a7553614e7a6c436731754f32482d772d5051675955675133396d533470416270677768734151757a53793636726d62756530434f30477a326f6f4d4752374b646d69727143613551594b4f546b33714d5a584b496942476d6534396c686f416b646a476f73465a48615f63714e39424e424f584b)](https://camo.githubusercontent.com/d42aab902ae670955ed94cb7682dba66b7eca8b0/68747470733a2f2f6c68352e676f6f676c6575736572636f6e74656e742e636f6d2f58506444452d343862366a6f7770744b5968446a7553614e7a6c436731754f32482d772d5051675955675133396d533470416270677768734151757a53793636726d62756530434f30477a326f6f4d4752374b646d69727143613551594b4f546b33714d5a584b496942476d6534396c686f416b646a476f73465a48615f63714e39424e424f584b)

Define n numbers in turn:

[![img](https://camo.githubusercontent.com/c2d833d280185e1e106df25cff484b4f74781421/68747470733a2f2f6c68332e676f6f676c6575736572636f6e74656e742e636f6d2f4f344c5037596944794659547870684e4e44795a6f432d513655434a6c30745367616865554662793143534531783671374a557a43725064364c4f714a336153354f4363423838746c597a775366616c5a6463793961616f6d646f5a2d546649446761424676385f7762307677633036557636663336336632477268793133676c79694f7a703564)](https://camo.githubusercontent.com/c2d833d280185e1e106df25cff484b4f74781421/68747470733a2f2f6c68332e676f6f676c6575736572636f6e74656e742e636f6d2f4f344c5037596944794659547870684e4e44795a6f432d513655434a6c30745367616865554662793143534531783671374a557a43725064364c4f714a336153354f4363423838746c597a775366616c5a6463793961616f6d646f5a2d546649446761424676385f7762307677633036557636663336336632477268793133676c79694f7a703564)

Then there are:

[![img](https://camo.githubusercontent.com/3126349bc32049980917b37ca2b410270b69d9bd/68747470733a2f2f6c68342e676f6f676c6575736572636f6e74656e742e636f6d2f453976676839324a4f6a4567597765535641672d4c7070713255507238654d6151505f6441685876302d695a784b353765336f5734434f794d73516339436946397650455077775549382d6875714651776e6763324951724c6d6c784f39547257622d5f5f6c6e7765466542644757494279734d73454942634d6d64776c357a544970504d65476f)](https://camo.githubusercontent.com/3126349bc32049980917b37ca2b410270b69d9bd/68747470733a2f2f6c68342e676f6f676c6575736572636f6e74656e742e636f6d2f453976676839324a4f6a4567597765535641672d4c7070713255507238654d6151505f6441685876302d695a784b353765336f5734434f794d73516339436946397650455077775549382d6875714651776e6763324951724c6d6c784f39547257622d5f5f6c6e7765466542644757494279734d73454942634d6d64776c357a544970504d65476f)

We know that we can find n sets of numbers for the above equation.

[![img](https://camo.githubusercontent.com/7a0513931a290c517e482a030dd23ab5a268ba10/68747470733a2f2f6c68342e676f6f676c6575736572636f6e74656e742e636f6d2f3176476b38354874617a497165563273783636577668454975654875415a4c4a336349783444484a63656c384e566e4f53694b6f4a5f693250695f6347494a5a6d757855507866446b304e575a6f586631722d6765516d457547333566785f6e7a45616b676a674b4d6c695a4d42444732334d7075667a4230553248596a64386459716a4c457148)](https://camo.githubusercontent.com/7a0513931a290c517e482a030dd23ab5a268ba10/68747470733a2f2f6c68342e676f6f676c6575736572636f6e74656e742e636f6d2f3176476b38354874617a497165563273783636577668454975654875415a4c4a336349783444484a63656c384e566e4f53694b6f4a5f693250695f6347494a5a6d757855507866446b304e575a6f586631722d6765516d457547333566785f6e7a45616b676a674b4d6c695a4d42444732334d7075667a4230553248596a64386459716a4c457148)

Corresponding

[![img](https://camo.githubusercontent.com/a0c50f406fcd57275c624cd42d3c7e9d6388037e/68747470733a2f2f6c68362e676f6f676c6575736572636f6e74656e742e636f6d2f744c4d5735466d64416e724d5054734370577a476c585830315f6d31426274715042556834723150725954767a674639414d7054376f6b3559385a4951626967457879714a7353757339332d5a2d574c466572636f6a5956446a31534e3631757834536f613759674c70734f475a576b5f327051525f7978595654436c384634587962555239647a)](https://camo.githubusercontent.com/a0c50f406fcd57275c624cd42d3c7e9d6388037e/68747470733a2f2f6c68362e676f6f676c6575736572636f6e74656e742e636f6d2f744c4d5735466d64416e724d5054734370577a476c585830315f6d31426274715042556834723150725954767a674639414d7054376f6b3559385a4951626967457879714a7353757339332d5a2d574c466572636f6a5956446a31534e3631757834536f613759674c70734f475a576b5f327051525f7978595654436c384634587962555239647a)

Satisfy:

[![img](https://camo.githubusercontent.com/acd0ba39aa0c007df7010148662f4a7d2e480555/68747470733a2f2f6c68332e676f6f676c6575736572636f6e74656e742e636f6d2f3839686d697a56584b565638683368734d6f586d4c6c753142754a62764378485a3959566f30586b734d31454d5753335a565752656b2d6e4a75716e496d6f4b544c3863616557593264637046685074474d4f707364784b5a7545717832423263587933484e677072782d2d442d68504a592d4e446e4672436e4642796e6445666f50504e342d73)](https://camo.githubusercontent.com/acd0ba39aa0c007df7010148662f4a7d2e480555/68747470733a2f2f6c68332e676f6f676c6575736572636f6e74656e742e636f6d2f3839686d697a56584b565638683368734d6f586d4c6c753142754a62764378485a3959566f30586b734d31454d5753335a565752656b2d6e4a75716e496d6f4b544c3863616557593264637046685074474d4f707364784b5a7545717832423263587933484e677072782d2d442d68504a592d4e446e4672436e4642796e6445666f50504e342d73)

In other words, the Borda score method is also unstable. So where is the problem, in fact, our assumptions constraints such fairness. In his paper, scholar Saari elaborated on the above issues. One of Saari's arguments is that Articles 4 and 5 of Arrow's conditions are “offset” with each other, so they have carried out the fourth rule. The amendment is as follows:

4'. Election results The ranking of A and B should be determined only by the relative order and distance of A and B in the file, regardless of any third party.

So under this assumption, Saari proves that the Borda Count election process is "fair" on the premise of more than two candidates! For specific technical details, please refer to [Saari's related papers](https://en.wikipedia.org/wiki/Donald_G._Saari#Papers). In other words, the Borda Count election process is better in this sense. Therefore, we try to adapt the BET voting system with the PoS system under this conclusion.

### III.BET voting system.

Next we will give a general description of the voting system:

It is assumed that the number of people participating in the election is N, K people vote.

Our voting rules are as follows:

1. For any voter, it is required to give a sequence Ln of the order in which the candidates fit or not.
2. The voter's voting weight is recorded as the number of tokens held and mortgaged by Pi.
3. Given a function F\(i\), the function returns a score for the different sequence numbers of the sequence. The specific function will be given below.
4. The rules for scoring any candidate are as follows:

Vk=∑F\(i,j\)\*Pi

1. Sort all candidates who participated in the election and draw the final selection sequence.

Assumptions:

In this program, we limit each voter, assuming that any voter can vote for the number of votes held in their hands, that is, Pi, and only one vote at a time, so we can treat each voter as a collection of voters with the same willingness to vote, each with only one vote, further seeing this becomes a model for the Borda count to vote for the Borda count. So it has the same theoretical characteristics as the Borda count system.

Of course, we can also follow the Borda count system exactly as follows:

1. Require each voting participant to mortgage the corresponding token,
2. Require it to give the corresponding selection sequence Ln
3. Given a function F\(i\), the function returns a score for the different sequence numbers of the sequence. The specific function will be given below.
4. The rules for scoring any candidate are as follows:

Vk=∑F\(i,j\)

But this does not reflect the advantages of the PoS system discussed above.

Further, for any token holder Pi, since he needs to vote \(sort\) all candidates, that is, he contributes to any candidate, but the degree of contribution is according to function F. Therefore, comparing the one-vote and multi-selection systems obviously weakens the role of the voting rights. The following figure compares the control with one-vote and multi-selection under different F functions:

[![img](https://camo.githubusercontent.com/ab2ae31a8bd9f84b54660e353addc54921b707e0/68747470733a2f2f6c68362e676f6f676c6575736572636f6e74656e742e636f6d2f643431532d6c6a59757257416e79626f416d76384a66555a636872337275556f576731723757657477416b4f7171626670645f4f394646707747746c48725f654152586a644d69475a62757147476c39316c5f59595665485278665f46564b6e697338754144373435785045423065322d3561773463706e544d38535f6e575050594c315457656a)](https://camo.githubusercontent.com/ab2ae31a8bd9f84b54660e353addc54921b707e0/68747470733a2f2f6c68362e676f6f676c6575736572636f6e74656e742e636f6d2f643431532d6c6a59757257416e79626f416d76384a66555a636872337275556f576731723757657477416b4f7171626670645f4f394646707747746c48725f654152586a644d69475a62757147476c39316c5f59595665485278665f46564b6e697338754144373435785045423065322d3561773463706e544d38535f6e575050594c315457656a)

The area below the line is the maximum vote for a voter voter

[![img](https://camo.githubusercontent.com/1ac48b714c73a3b0facf58a7c952da66e5043ce5/68747470733a2f2f6c68342e676f6f676c6575736572636f6e74656e742e636f6d2f426a4577655242476c4d6143476c5739625a335f6c336b6b7865324d6463494c32467547576d5347516a434b72417644332d44374b335a5938316d704246502d30656b6a65332d735a772d3633314e3379496e4a42774d4a325f45575242587a71647572476c6c647042466a6d647243386f68784537722d6349693736716f4c6b6c33464e502d41)](https://camo.githubusercontent.com/1ac48b714c73a3b0facf58a7c952da66e5043ce5/68747470733a2f2f6c68342e676f6f676c6575736572636f6e74656e742e636f6d2f426a4577655242476c4d6143476c5739625a335f6c336b6b7865324d6463494c32467547576d5347516a434b72417644332d44374b335a5938316d704246502d30656b6a65332d735a772d3633314e3379496e4a42774d4a325f45575242587a71647572476c6c647042466a6d647243386f68784537722d6349693736716f4c6b6c33464e502d41)

The area below the line is the maximum vote when F is the Borda count system.

[![img](https://camo.githubusercontent.com/b78c32ebe11b316910246b09d67f68fbe06cc302/68747470733a2f2f6c68362e676f6f676c6575736572636f6e74656e742e636f6d2f674d653334493130476c69446943377936615973427a476a457137486a50594e714a74343636797854556862334f6a5378516c34306b657236364a364f4861526450695a3565413047445178634e697643614a4f576a366f4c7857525332786b314a34597262543167624a4561736659335078354b5239754e384776365743665735376e67315f38)](https://camo.githubusercontent.com/b78c32ebe11b316910246b09d67f68fbe06cc302/68747470733a2f2f6c68362e676f6f676c6575736572636f6e74656e742e636f6d2f674d653334493130476c69446943377936615973427a476a457137486a50594e714a74343636797854556862334f6a5378516c34306b657236364a364f4861526450695a3565413047445178634e697643614a4f576a366f4c7857525332786b314a34597262543167624a4561736659335078354b5239754e384776365743665735376e67315f38)

The maximum area below the line is the voting maximum when F is X^\(-σ\)

Although not rigorous, you can intuitively feel the difference between them.

Next, we will illustrate the features and advantages of the program through a few simple examples:

1. Suppose there are three voters A, B, and C. For the sake of discussion, let's assume that the candidates are the same three, and assume that they vote for themselves. Our voting principle is to choose two of the three to win.

We assume that A, B, and C hold the number of tokens a, b, and c, respectively. If we assume conspiracy in a and b, if EOS's current voting system is adopted, c will lose the final right as long as a+b&gt;c. But under the BET system, you need a+2b&gt;2c to get the corresponding result. In the case where the differences among the candidates are not different, a and c can be elected.

1. Consider another example of bribery. Let's assume that there is a large A with 2,000,000 tokens. The support of other candidates is only between 1,000,000 and 6,000,000. If the EOS strategy is adopted, then the other candidates cannot agree. Under the premise, A can control the entire order of the elected person. Due to the strong control of A, many candidates will choose to trade with A, which will eventually lead to the further strengthening of A's control.

For the BET system, the situation will be different. For example, we use \(n+1-i\)/n as the F function, n is assumed to be 25, then for the big A, it is for the i support. The contribution value provided by the account is \(n+1-i\)/n\*a. For example, when i is 20, the contribution value is 4,800,000, that is, when there is a token held by the voter in the hand, the token exceeds the value.

Choosing to work with this token holder is a better strategy than working with A. Therefore, this can weaken the control power of A to a certain extent and at the same time ensure the interests of many stakeholders. At the same time, because the plan is necessary to fill the gap, the voter is maximizing the profit for the benefit of the rational person. In addition to yourself, the remaining votes will be voted for the most stable candidates for the system, thus ensuring the security and stability of the system.

### IV. Summary

The design is a further exploration of the existing EOS voting system, with the research results of Saari et al., which can make the BET voting system more perfect, but as the Arrow impossible theorem says, when it is limited to certain conditions, the perfect voting plan does not exist. So we hope to better the current model under reasonable assumptions.

