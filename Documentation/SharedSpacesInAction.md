# SharedSpaces in Action

Let's look at SharedSpaces in action.

<div style="text-align: center; padding: 10pt;">
    <img src="./Media/screenshots/1a.jpg" width="250">
    <img src="./Media/screenshots/1b.jpg" width="250">
</div>

When Alice starts SharedSpaces, she begins alone in her private lobby. She is the master client and host of the lobby, as indicated by the star next to her name.

<div style="text-align: center; padding: 10pt;">
    <img src="./Media/screenshots/2a.jpg" width="250">
    <img src="./Media/screenshots/2b_id.jpg" width="250">
    <img src="./Media/screenshots/2c.jpg" width="250">
    <img src="./Media/screenshots/2d.jpg" width="250">
</div>

Alice wants Bob to form a group with her so they can be together between matches. She steps on the invite panel switch and sends him an invitation from her lobby. By accepting, SharedSpaces starts on Bob's headset with a deeplink message that lets him join Alice in-game. From now on, Bob will have the same lobby session ID as Alice, and they will share the same lobby.

<div style="text-align: center; padding: 10pt;">
    <img src="./Media/screenshots/3a.jpg" width="250">
    <img src="./Media/screenshots/3b.jpg" width="250">
    <img src="./Media/screenshots/3c.jpg" width="250">
    <img src="./Media/screenshots/3d.jpg" width="250">
</div>

Bob goes through the blue door to start a private match, followed by Alice. They end up in the same Blue Room, and they now have the same match session ID that corresponds to their private room. Since Bob was there first, he is the one hosting the room, and Alice is connected to him.

<div style="text-align: center; padding: 10pt;">
    <img src="./Media/screenshots/4a_id.jpg" width="250">
    <img src="./Media/screenshots/4b_id.jpg" width="250">
    <img src="./Media/screenshots/4c.jpg" width="250">
    <img src="./Media/screenshots/4d.jpg" width="250">
</div>

Alice decides to invite her friend Charlie to join their match, and he happens to be in his lobby when he accepts the invitation. Charlie has his match session ID updated with the private match ID, but on the other hand, he still retains his lobby session ID. He is still part of a different group.

<div style="text-align: center; padding: 10pt;">
    <img src="./Media/screenshots/5a.jpg" width="250">
    <img src="./Media/screenshots/5b.jpg" width="250">
    <img src="./Media/screenshots/5c.jpg" width="250">
</div>

When Bob leaves the blue room, Photon notifies Alice and Charlie that the master client has changed. A host migration is needed: Alice opens a new listen-server since she is the new master client of the blue room, and Charlie connects to her.

As for Bob, he started hosting his group lobby.

<div style="text-align: center; padding: 10pt;">
    <img src="./Media/screenshots/6a.jpg" width="250">
    <img src="./Media/screenshots/6b.jpg" width="250">
</div>
<div style="text-align: center; padding: 10pt;">
    <img src="./Media/screenshots/6c_id.jpg" width="250">
    <img src="./Media/screenshots/6d_id.jpg" width="250">
    <img src="./Media/screenshots/6e_id.jpg" width="250">
</div>

Now, when Charlie leaves the blue room, he does not join Bob. They are not part of the same group since they have different lobby session IDs. Instead, he goes back to his separate lobby. This can be checked by stepping on the roster panel switch, and you will see your different groups explicitly listed.

<div style="text-align: center; padding: 10pt;">
    <img src="./Media/screenshots/7a.jpg" width="250">
    <img src="./Media/screenshots/7b.jpg" width="250">
</div>

In the case of Alice, therefore, going back to the lobby means that she will rejoin Bob, who is waiting for her.

<div style="text-align: center; padding: 10pt;">
    <img src="./Media/screenshots/8a_id.jpg" width="250">
    <img src="./Media/screenshots/8b_id.jpg" width="250">
    <img src="./Media/screenshots/8c.jpg" width="250">
    <img src="./Media/screenshots/8d.jpg" width="250">
</div>

To have Charlie join their group, Alice or Bob simply need to send him an invitation from their lobby. Again, by accepting an invitation to a lobby, you also accept joining a group. Charlie's lobby session ID is updated, and the three of them will now share the same lobby between matches.
