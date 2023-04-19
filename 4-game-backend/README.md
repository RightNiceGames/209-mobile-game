# 4 Game Backend

In this chapter, we'll set up a simple Game Backend using Google Firebase. It has many features like:
- Authentication
- Storage
- Leaderboards
- Analytics

## Backend
A backend is a separate software that game clients can connect to in order to
- save information
- retrieve information
- connect with other game clients

## Authentication
Authentication describes the process of finding out who's making a connection
- Username & Password
- DeviceId
- Third-Party Secrets

## Authorization
Authorization describes validation of who is allowed to execute what action
- e.g. only Clan Leader can delete a clan
- e.g. only opponents can attack each other
- e.g. only Player #1234 can access Player #1234's inventory

## Firebase
Firebase is Google's Backend as a Service (BaaS). There is many alternatives.
- Accelbyte
- AcceleratXR
- Amazon Gametech
- Beamable
- Brainloud
- Edgegap
- Epic Online Services
- Fish Networking
- Lootlocker
- Microsoft PlayFab
- Nakama
- Photon
- Smartfox
- Unlockd
- Unordinal
- Xtralife
- Steam Services
- ...

## Never Trust the Client
The basics of Cheat Protection teach us: Never Trust the Client! It can be:
- outdated (forgot to patch)
- corrupted (files broke while copying, hardware errors)
- impersonated (someone trying to impersonate another client)
- hacked (by someone else to steal data / valuables)
- hacked (by the user to cheat)

How do you achieve this?

### Validate the Client's input:

Wrong:
- The client says it placed a Tower at Position 5. It must be true.
Right:
- Validate that the Player owns the Tower.
- Validate that the Position exists.
- Validate that the Position is Empty.
- Validate that the Player is allowed to move buildings around.
- Validate that Towers are movable.

### Use Encrypted Connections
Usually, Third-Party Backend SDKs already provide this Feature.

### Communicate Actions, Not Results

Wrong:
- Client tells Backend that he got 200 Gold from a Loot Box.

Correct:
- Client tells Backend that he completed a Level.
- Backend tells Client what his rewards for the level are.

### Take as Much Data as Possible From the Backend

Wrong:
- Client tells Backend that his Tower after upgrading has 500 Health.

Right:
- Client tells Backend that he finished his Tower Upgrade.
- Backend increments Tower Level by 1. 3->4
- Backend checks the Game Data for how much Health a Tower Level 4 has.
- Backend finds that it's 500 and uses that Value.

## Avoid Redundancy

Make sure that all information is in one place only. This will make it it a lot easier to update information later and it avoids inconsistent information.

Imagine a Game where the Player can build and upgrade towers.

Wrong SaveGame:
```json
{
    "buildingType":"Tower",
    "level":5,
    "position":5,
    "maxHealth":200,
    "damage":10
},
{
    "buildingType":"Tower",
    "level":5,
    "position":8,
    "maxHealth":200,
    "damage":10
}
```

Right SaveGame:
```json
{
    "buildingType":"Tower",
    "level":5,
    "position":5,
},
{
    "buildingType":"Tower",
    "level":5,
    "position":8,
}
```

The other values can be found in the Config for Tower Level 5 which is not unique for a single player:
```json
{
    "buildingType":"Tower",
    "level":5,
    "maxHealth":200,
    "damage":10
}
```

This way, if you release a new update that reduces this overpowered tower's damage from 10 to 9, you only need to do it in that Tower's Config. And not in every single player's save games.

## Concurrency
When working with Networking or File Systems, the time will come at which you need to run processes concurrently a.k.a. in the background and do something when they're finished.

[Link to Slides]()