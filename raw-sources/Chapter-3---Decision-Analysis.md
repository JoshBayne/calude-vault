# Chapter 3.2 - Follow Along

Created: 2023-01-23 10:37:50 -0600

Modified: 2023-01-23 10:38:18 -0600

---

![CHAPTER 3 ILLUSTRATED EXAMPLES ](../../media/DSCI-DSCI-3331-Chapter-3.2---Follow-Along-image1.png){width="8.375in" height="6.479166666666667in"}



![IN THIS PRESENTATION ILLUSTRATED EXAMPLES: • DECISION MAKING UNDER UNCERTAINTY DECISION MAKING UNDER RISK • DECISION TREES ](../../media/DSCI-DSCI-3331-Chapter-3.2---Follow-Along-image2.png){width="8.375in" height="6.479166666666667in"}



![TYPES OF DECISION-MAKING ENVIRONMENTS • Type I: Decision making under certainty. Decision maker knows with certainty the consequences of every alternative or decision choice. • Type 2: Decision making under uncertainty. The decision maker does not know the probabilities of the various outcomes. • Type 3: Decision making under risk. The decision maker does know the probabilities of the various outcomes. ](../../media/DSCI-DSCI-3331-Chapter-3.2---Follow-Along-image3.png){width="8.375in" height="6.479166666666667in"}



![JOHN THOMPSON'S BACKYARD STORAGE SHEDS Define problem List alternatives Identify outcomes List payoffs Select a model Apply model and make decision To manufacture or market backyard storage sheds 1. Construct a large new plant 2. A small plant 3. No plant at all The market could be favorable or unfavorable for storage sheds List the payoff for each state of nature/decision alternative combination Decision tables and/or trees can be used to solve the problem Solutions can be obtained and a sensitivity analysis used to make a decision ](../../media/DSCI-DSCI-3331-Chapter-3.2---Follow-Along-image4.png){width="8.375in" height="6.479166666666667in"}



![PAYOFF TABLE FOR THOMPSON State of Nature Alternatives Construct large plant Construct small plant Do nothing Favorable Market 200,000 I OO,OOO Unfavorable Market - 180,000 -20,000 ](../../media/DSCI-DSCI-3331-Chapter-3.2---Follow-Along-image5.png){width="8.375in" height="6.479166666666667in"}



![DECISION MAKING UNDER UNCERTAINTY •MAXIMAX •MAXIMIN •EQUALLY LIKELY (LAPLACE) •CRITERION OF REALISM •MINIMAX REGRET ](../../media/DSCI-DSCI-3331-Chapter-3.2---Follow-Along-image6.png){width="8.375in" height="6.479166666666667in"}



![MAXIMAX- BEST(OF BEST) Optimistic. Greedy State of nature Alternatives Construct large plant Construct small plant Do nothing Favorable Market 200,000 I OO,OOO Unfavorable Max Market - 180,000 -20,000 ](../../media/DSCI-DSCI-3331-Chapter-3.2---Follow-Along-image7.png){width="8.375in" height="6.479166666666667in"}



![MAXIMIN- BEST(OF WORST) Pessimistic. Conservative State of nature Alternatives Construct large plant Construct small plant Do nothing Favorable Market 200,000 I OO,OOO Unfavorable Min Market - 180,000 -20,000 ](../../media/DSCI-DSCI-3331-Chapter-3.2---Follow-Along-image8.png){width="8.375in" height="6.479166666666667in"}



![CRITERIA OF REALISM CR= a*(row max)+(l- a)*(row min) ; with a given a = 0.8 State of nature Alternatives Construct large plant Construct small plant Do nothing Favorable Market 200,000 I OO,OOO Unfavorable Market -180,000 -20,000 CR (a = 0.8) ](../../media/DSCI-DSCI-3331-Chapter-3.2---Follow-Along-image9.png){width="8.375in" height="6.479166666666667in"}



![EQUALLY LIKELY Averaging all possibilities State of nature Alternatives Construct large plant Construct small plant Do nothing Favorable Market 200,000 I OO,OOO Unfavorable Market - 180,000 -20,000 Average ](../../media/DSCI-DSCI-3331-Chapter-3.2---Follow-Along-image10.png){width="8.375in" height="6.479166666666667in"}



![MINIMAX REGRET Choose the alternative that minimizes the maximum opportunity loss. 200,000 . -180,000 100,000 ; -20,000 First, build the Regret Table. Payoff Table State of nature Favorable Market Alternatives• Construct large plant Construct small plant Do nothing Regret Table Computed Cell= Best --- original cell value State of nature Favorable Unfavorable Unfavorable Market Market Market Alternatives Construct large plant Construct small plant Do nothing ](../../media/DSCI-DSCI-3331-Chapter-3.2---Follow-Along-image11.png){width="8.375in" height="6.479166666666667in"}



![MINIMAX REGRET- CONT. Now that we have built the regret or opportunity loss table, we can find the minimum of the Maximum regret State of nature Alternatives Construct large plant Construct small plant Do nothing Favorable Market I OO,OOO 200,000 Unfavorable Market 180,000 20,000 Max (regret) ](../../media/DSCI-DSCI-3331-Chapter-3.2---Follow-Along-image12.png){width="8.375in" height="6.479166666666667in"}



![DECISION MAKING UNDER RISK EXPECTED MONETARY VALUE • EXPECTEDVALUE OF PERFECT INFORMATION ](../../media/DSCI-DSCI-3331-Chapter-3.2---Follow-Along-image13.png){width="8.375in" height="6.479166666666667in"}



![EXPECTED MONETARY VALUE EXPECTED MONETARY VALUE: EMV(ALTERNATIVE N) = PAYOFF, * P(SI) + PAYOFF2 * P(S2) + . . + PAYOFFN * P(SN) ](../../media/DSCI-DSCI-3331-Chapter-3.2---Follow-Along-image14.png){width="8.375in" height="6.479166666666667in"}



![EXPECTED MONETARY VALUE (EMV) Averaging all possibilities State of nature Alternatives Construct large plant Construct small plant Do nothing Probabilities Favorable Market 200,000 I OO,OOO 0.5 Unfavorable EMV Market -180,000 -20,000 0.5 ](../../media/DSCI-DSCI-3331-Chapter-3.2---Follow-Along-image15.png){width="8.375in" height="6.479166666666667in"}



![EXPECTEDVALUE OF PERFECT INFORMATION •EXPECTEDVALUE OF PERFECT INFORMATION (EVPI) PLACESAN UPPER BOUND ONWHAT ONEWOULD PAY FOR ADDITIONAL INFORMATION. •EVPI IS THE EXPECTEDVALUEWITH PERFECT INFORMATION (EVIPI) MINUS THE MAXIMUM EMV. EVIPI=BEST PAYOFF OF PAYOFF OF P(S2) +... +BEST PAYOFF OF P(SN) EVPI = EVIPI - MAX(EMV) Expected value with Expected value with no perfect information additional information ](../../media/DSCI-DSCI-3331-Chapter-3.2---Follow-Along-image16.png){width="8.375in" height="6.479166666666667in"}



![EXPECTEDVALUE OF PERFECT INFORMATION First Compute the expected value with perfect information EVIPI State of nature Alternatives Construct large plant Construct small plant Do nothing Probabilities Best Payoff perfect Favorable Market 200,000 I OO,OOO 0.5 Unfavorable Market - 1 80,000 -20,000 0.5 EMV ](../../media/DSCI-DSCI-3331-Chapter-3.2---Follow-Along-image17.png){width="8.375in" height="6.479166666666667in"}



![EXPECTEDVALUEWITH PERFECT INFORMATION Now that we have EVIPI, we can conclude the value of EVPI EVPI = EVIPI - max(EMV) EVIPI= 100,000 Max 40,000 EVPI OO,OOO 60,000 ](../../media/DSCI-DSCI-3331-Chapter-3.2---Follow-Along-image18.png){width="8.375in" height="6.479166666666667in"}



![DECISION TREES DECISION TREES ARE MOST BENEFICIAL WHEN A SEQUENCE OF DECISIONS MUST BE MADE. ALL INFORMATION INCLUDED INA PAYOFF TABLE IS ALSO INCLUDED INA DECISION TREE. ](../../media/DSCI-DSCI-3331-Chapter-3.2---Follow-Along-image19.png){width="8.375in" height="6.479166666666667in"}



![DECISION TREES- STRUCTURE A GRAPHICAL REPRESENTATIONWHERE: A DECISION NODE (INDICATED BY A SQUARE [3 ) FROM WHICH ONE OF SEVERAL ALTERNATIVES MAY BE CHOSEN. A STATE-OF-NATURE NODE (INDICATED BY A CIRCLE ) OUT OF-WHICH ONE STATE OF NATUREWILL OCCUR. ](../../media/DSCI-DSCI-3331-Chapter-3.2---Follow-Along-image20.png){width="8.375in" height="6.479166666666667in"}



![THOMPSON DECISION TREES ](../../media/DSCI-DSCI-3331-Chapter-3.2---Follow-Along-image21.png){width="8.375in" height="6.479166666666667in"}



![Ⅴ장0 ](../../media/DSCI-DSCI-3331-Chapter-3.2---Follow-Along-image22.png){width="8.375in" height="6.479166666666667in"}






















