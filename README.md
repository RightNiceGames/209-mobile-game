# 209 Mobile Game

## Premise
In this project you will work on multiple collectible mobile games. You will implement monetization solutions, design and balance an economy as well as gameplay.

As such, the general metagame loop will be provided, as well as the general framing conditions for your gameplay loop, it will fall to you to interpret and implement these in such a way that you can meet the project scope goals.

### Metagame
Right out of the playbook for collectible card games we'll have
- Draft/Summoning mechanic
- Gacha Collectible Mechanic
- Fusion Upgrade Mechanic 
- Tiered Currency Mechanic
- Rewarded Ads
- In-App Purchases

### Gameplay
The gameplay will involve the items gained from the metagame loop.

What's important is that you Parametrize the gameplay so you can properly balance it by tweaking some numbers rather than changing mechanics.

## Grading

### Passing
Group Deliverables:
- Baseline Milestone Achieved
- Android Build
- Description of the project in `README.md`
- Screenshots, Video in `README.md`
- Group Contract
- Weekly Sprint Retro Documentation
  - List the Problems that were analyzed
  - List the Actions to take in the next sprint

Individual Deliverables:
- Post Mortem, at least 500 words, Recommended: 1000
  - Introduction
  - Successes
  - Challenges
  - Reflections
  - Conclusions

### Excellent
Group Deliverables:
- Advanced Milestone Achieved
  - Points of the Advanced Milestone can be renegotiated and swapped with points from the Update Milestone

Individual Deliverables:
- Post Mortem, at least 1000 words
  - Thorough Reflections and Learnings
  - Meaningful Contributions Documented 

## Grouping
Group sizes are flexible for this project. The goal of this project is to promote exchange with new team mates and provide rewarding challenges.

The roles of each group are not fixed, though. And each group may rely on other groups' contributions. It will be up to you to determine your group's strengths and decide, what components (see below) your team will take on.

### Many Small Teams, Individual Projects
One great option is to work in many smaller teams. This will result in lesser management overhead and higher flexibility in the planning. However, time and resources are very limited and you'll have to implement many features just to have them done and won't have a lot of opportunity to polish, iterate and specialize.

### One large Project, Multiple Department Teams
Another option is to collaborate in one big project with specialized departments such as
- Backend/Integrations
- Core/Gameplay
- User Interface
- Metagame

## Challenges
The general goal for this project is to release a game on the `Google Play Store`, so you'll have to not only deliver the software, but also jump through all the hoops that come with releasing a product to a store such as app-icons, privacy policies, terms of use, etc. 

You will need to implement the various systems and assets such as:
- Integrate IAPs
- Integrate Rewarded Ads
- Implement Metagame Screens & Mechanics
- Implement Gameplay Scenes & Mechanics
- Build and Deploy on Google Play
- Integrate Analytics Solution & Hooks

## Teacher's Role
Your teacher will take on the mantle of Technical Director and executive producer.

## Scope
The scope will be divided into "baseline", "advanced", and "update" milestones.

You should not work on things in "advanced" before completing "baseline", and not work on "update" before completing "advanced", and not work on anything that's not in a milestone at any time during the project.

If you need items to be added or removed to realize your vision, you need to negotiate for it with your teacher. 

You are free to break down the scope into tickets for your backlog as you see fit, we highly recommend you review past projects and/or ask for guidance on how to structure your backlog.

### Definition Of Done
While every team may add to this definition, it should serve as the baseline definition of done.

A feature is done if:
- It has passed its associated test cases.
- It does not break another feature.

## Baseline Milestone
These statements should be TRUE as a result of your work on the baseline milestone:

|ID|Label|Description|
|--|-----|-----------|
|1|Project Builds Shippable App|You have a project set up that builds into an app that can be deployed to a mobile device via a shop, including an app-icon, EULA, TOS, PP|
|2|User Can Buy Soft Gacha|Your player can find a gacha/draft/summon feature and receive randomized items from it, storing them in an inventory to review at a later time.|
|3|User Can Use Items In Gameplay|Your player can find a gameplay feature that uses the items in their inventory as game pieces.|
|4|User Can Earn Soft Currency Through Gameplay|Your player can earn soft currency from some activity tied to the gameplay loop such as completing it or winning.|
|5|User Can Earn Soft Currency From Ads|Your player can find a feature where they can earn a soft currency amount from watching ads. The feature is limited by cooldowns.|
|6|Data Persistence|The player's progress is persistent. Closing and Launching the Game will not affect his inventory or resources.|

## Advanced Milestone
These statements should be TRUE as a result of your work on the advanced milestone:

|ID|Label|Description|
|--|-----|-----------|
|1|User Can Buy Premium Currency|User can find an in-app shop where they can purchase premium currency.|
|2|User Can Buy Premium Gacha|Your player can find a premium gacha/draft/summon feature and receive randomized items from it, it should contain better items or better chances for better items than the soft currency version.|
|3|User Can Earn Login Bonus|Your player receives rewards for playing the game based on a scheme incentivizing recurrent activity.|


## Update Milestone
These statements should be TRUE as a result of your work on the update milestone:

|ID|Label|Description|
|--|-----|-----------|
|1|User Can Compete With Others|Your user can find a competition feature such as a league and/or leaderboard.|
|2|User Can Play Against Others|Your user can find a gameplay mode where they directly challenge other players either synchronous or asynchronous or through a leaderboard.|
|3|User Can Invite Social Contacts|Your user can invite others from their social network such as Facebook to play the game.|
|4|User Can Upgrade Through Fusion|Your player can find a feature where they can combine same or similar items into more powerful versions.|
|5|User Can Store Data in Backend|Your player can find a feature that allows them to back-up their data online instead of on their device.|
|6|User Can Sell Items For Soft Currency|Your player can find a feature where they can convert some of their items to some soft currency.|

## Components

### Metagame
- Currency
- Gacha
- Inventory

### Gameplay
- Rewarding gameplay

### Integrations
- In-App Purchases
- Ads
- Google Play Store
- Apple App Store
- Time-Tracking (Login-Bonus, Cooldowns)
- Persistence

### Backend
- Authentication
- Online-Persistence
- Social Features
