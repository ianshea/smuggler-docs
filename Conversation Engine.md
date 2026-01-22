Conversation Engine for Interactions.

How are most dialogue/conversation elements created currently?
Most seem to lack any depth at all. But from what I can see is people love to build relationships in games.

Is there an approach to take to designing conversations for the game, be it narrative or just normal NPC interactions that can provide more depth without relying on some kind of API AI interactions. Which seems like the lazy go to.

I'd imagine a system connected to global state variables; weather, time of day for example, along with some personal relationship and previous interaction data.

*Example:*

Location: Riverton

Time : Afternoon
Weather: Rain
Previously Bought: Mushrooms, Herbs

Vendor: Mushroom Stall Vendor
Name: Kenneth

Variety Greetings:
*Afternoon mate, shite weather to be out in. Looking for more Mushrooms?*
*Rainy afternoon friend, need some more herbs?*

- Talk
- Yes, let's trade
- No, what else you got?
- Quest/Narrative/etc. (if applicable)

Player chooses **Trade** - Opens screen with quantity of mushrooms from last order.
Choose No - Open Trade Screen Empty
Choose Talk, maybe it leads to conversation options that unlock opportunities, etc.

## Random Questions

Am I over thinking this whole thing? And should I scope it down?

How do we compose a variety of message like that? 
How do we add variations and not be overly repetitive?
How do we give various tones to different types of regional characters when world building?
How do we create a framework for it that a writer could use to generate the various lines and characters?
Over time does the character get recognized and NPC greets by name?
Can we find a bunch of generic/variety of friend, mate, 
	If we did... could we do it regionally? It's either just variables or huge scope.
## On Repeated Interactions

I imagine the system might have some kind of descending system of message length.

A longer message, and then more of a you again type greeting, something shorter, then just skip it after a few times.

--

