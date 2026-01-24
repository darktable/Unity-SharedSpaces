# Overview of SharedSpaces

<div style="margin: auto; width: 60%; padding: 10pt;">
<table>
<tr style="background-color:#FFEEEE;">
    <td style="border:0px;"><b>Oculus</b></td>
    <td style="border:0px;">Group presence with <i>destination</i>, <i>lobby</i>, and <i>match</i> ids.</td>
</tr>
<tr style="background-color:#EEFFEE;">
    <td style="border:0px;"><b>Photon Realtime</b></td>
    <td style="border:0px;">Transport via a <i>room</i> named after the <i>lobby</i> or <i>match</i> id.</td>
</tr>
<tr style="background-color:#EEEEFF;">
    <td style="border:0px;"><b>Netcode for GameObjects</b></td>
    <td style="border:0px;">Replication between <i>room members</i> with <i>the master client</i> as host.</td>
</tr>
</table>
</div>

## *A Private Lobby Connected to Rooms*
<div style="text-align: center; padding: 10pt;"><img src="./Media/layout.png" align="middle" width="600"></div>

SharedSpaces consists of several connected levels known as destinations. At the center is your personal lobby with doors leading to surrounding matches. The matches on the left are private and accessible only from your lobby. The match on the right is public and accessible from any lobby.

## *Social Layer - Destination, Lobby & Match Session IDs*

<div style="text-align: center; padding: 10pt;"><img src="./Media/presence.png" align="middle" width="750"></div>

This layout directly represents the new group presence APIs. To reach a SharedSpaces destination, we first set your destination and a pair of session identifiers in your group presence: one for your lobby session ID, which rarely changes, and one for your match session ID, set only when you join a match.

Destinations are specific areas of your application defined on the [Oculus dashboard](https://developers.meta.com/horizon/manage/) under **Platform Services > Destinations**. The lobby session ID represents a group of people who want to stay together between games and possibly play as a team during matches. The match session ID is shared by people currently playing a match together, whether on the same team or not.

<div style="text-align: center; padding: 10pt;"><img src="./Media/invitation_to_lobby.png" align="middle" width="600"></div>

When you launch SharedSpaces, you start in your private lobby, for which we create a unique ID. To form a group before and after matches, invite people to share your lobby. If they accept, their lobby session ID updates to match yours, and whenever you're in the lobby simultaneously, you'll be together in the same space.

Think of the lobby as the base camp for your group. Different groups always return to their respective lobbies after matches.

<div style="text-align: center; padding: 10pt;"><img src="./Media/private_room.png" align="middle" width="700"></div>

Group members can travel anytime between your lobby and their private matches. This only affects the match session IDs of their group presence.

<div style="text-align: center; padding: 10pt;"><img src="./Media/invitation_to_match.png" align="middle" width="700"></div>

You can also grant access to your private match to anyone. Invite them from that match, and they join you upon accepting the invitation. In SharedSpaces, accepting a match invitation only affects your match session ID, not your lobby session ID.

<div style="text-align: center; padding: 10pt;"><img src="./Media/respective_lobbies.png" align="middle" width="650"></div>

When they leave the match through the lobby door, users return to their separate lobbies if they are not in the same group.

<div style="text-align: center; padding: 10pt;"><img src="./Media/public_room.png" align="middle" width="650"></div>

SharedSpaces also features a purple room representing a public match accessible from all lobbies. Anyone can move from their lobby to the purple room anytime, affecting only their match session ID. It's a space to meet people outside your group without prior invitation.

## *Transport Layer - Photon Rooms*

To connect users, Photon uses the concept of a room. People in the same match or lobby instance are in the same Photon room, allowing data to flow between them. The transport layer routes packets between users, who are likely behind network firewalls.

<div style="text-align: center; padding: 10pt;"><img src="./Media/session_to_room.png" align="middle" width="650"></div>

Photon rooms have *unique names*. The room name comes directly from the social layer: we use your match session ID if you have one, or your lobby session ID otherwise.

A key feature of the Photon room system is tracking the oldest member, called the "master client," identified with stars.

<div style="text-align: center; padding: 10pt;"><img src="./Media/photon_join_or_create.png" align="middle" width="650"></div>

Consider Alice, Bob, and Charlie entering the Purple room. Charlie joins first, creating the room and becoming its **master client**. Alice and Bob join shortly after as **normal clients**.

<div style="text-align: center; padding: 10pt;"><img src="./Media/photon_notification.png" align="middle" width="650"></div>

If Charlie, the master client, leaves, a new master client is selected, and all remaining clients are notified. This feature is crucial for the next networking layer.

## *Game Replication Layer - Netcode for GameObjects*

Extensive documentation on Netcode for GameObjects is available on the [Unity Documentation site](https://docs.unity3d.com/Manual/multiplayer.html).

For applications like SharedSpaces, we can host the server on one of the headsets as a listen-server. In this mode, the game acts as both a server and its first connected client, accepting connections from other players.

For each room, we select one user as the listen-server. This decision comes from the transport layer: the **master client** of the corresponding Photon room becomes our host.

<div style="text-align: center; padding: 10pt;"><img src="./Media/photon_to_ue4_1.png" align="middle" width="650"></div>

When the hosting player leaves, we perform a host migration. Here, Alice leaves the purple room. Photon selects Bob as the new master client. The remaining room members are notified, and they reestablish their Unity connections.

<div style="text-align: center; padding: 10pt;"><img src="./Media/photon_to_ue4_2.png" align="middle" width="650"></div>

We end up with two Photon rooms; the Purple room is now hosted by Bob, with Charlie and Donna connected to him. Alice just left the room through the door to her lobby, but since she is the only one there, she becomes both the master client and host of her group lobby.
