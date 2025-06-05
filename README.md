# spurs_transfer_scout

### Proposal
* Tottenham weakness filling: 
  * Based on current squad weaknesses and performance, determine ideal players to sign during the transfer window. 
  * Would involve two parts: 
    1. Identification of squad weaknesses and needs
      * Deficiency analysis - can be done by comparing Spurs' metrics to the league average or an average across Europe, or the average across the Top 6 (minus us). These would be team-level metrics such as average xG per game, goals scored per game, and other creation or defensive metrics.
        * Can involve ML - clustering to see where Spurs fit; if we cluster with lower-performing teams in certain metrics (e.g., defensive stability), those are deficiencies. K-means
        * Can also train a supervised model to look at feature importances when predicting match outcome. E.g., defensive errors having a high feature importance may mean that there are defensive deficiencies that should be addressed in the window. SHAP?
      * Ultimately want to provide a dataset of deficiencies within the team; these deficiencies need to be translated into player profiles for part 2
    2. Recommendation of players who address weaknesses and fit needs
      * How to account for playing style?
      * Feature engineering - create features (metrics) based on the deficiencies, e.g., tackle success rate for defenders
      * Can build a supervised ML model (recommendation model) to compute a "fit score" for each player. Another option that I can use in conjunction w that is clustering - can cluster players by all the features so that players w similar playing styles are close together. Plot this in 3 or 2D, where engineered "ideal" signings are placed on the plot s.t. players nearby are likely the best signings. 
      * I want model explainability as well - if you click on the profile of a certain player, I want it to be clear why that player is recommended. Can use SHAP.
      * Not sure how I would take into account transfer budget and estimated player costs - any way to pull player estimated worths?
      * Cross-reference w transfer rumours - not sure if there is a platform that has a list of transfer rumours (maybe betting platforms; odds can be taken into account too then) but if not we can do NER from tweets pulled from SpursExpress, HotspurRelated, etc. 
      * Recommendations must also take into account logistics, e.g., age, nationality, contracts
      * It would be cool if, whenever you click on a player name, a profile shows up that contains: 
        * Basic information: name, position, nationality, age, picture, current team, contract status
        * Explanation of why they were recommended: fit score, highlighted metrics
          * Radar plot of their metrics compared to the squad average in that position?
  * Ideally, this should be applicable to every club, but I'd like to start small. I can try to modularize code from the start.