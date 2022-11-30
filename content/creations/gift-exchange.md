---
title: gift-exchange.py
date: 2022-11-30
---

This year for Christmas, my siblings, wife, and I decided to each give a gift to one other person rather than having everyone give to everyone else. I'm a nerd, so instead of simply drawing names (what are we, animals?!), I wrote a little Python script to generate matches for us.

<!--more-->

The script is quite basic and not terribly optimized (because it doesn't need to be). The only "special feature" is that I made it possible to specify `bad_matches` to prevent my wife and I from giving to each other -- we'll already be giving to each other outside of this gift exchange.

Here's the script, with fictional names and excessive comments:

```python
import random

# list of people giving/receiving gifts
people = ['Tom', 'Sally', 'Bill', 'Louise', 'Jennifer', 'Carl']

# disallowed matches -- person p cannot give to anyone in bad_matches[p]
bad_matches = {'Bill': ['Louise'], 'Louise': ['Bill']}

# sort people so that those with disallowed matches appear first and therefore
# have a greater chance of finding a valid match in the possible remaining
# receivers
people.sort(key=lambda p: 0 if p not in bad_matches else len(bad_matches[p]),
            reverse=True)

# helper function to check if giver can give to receiver
def can_match(giver, receiver):
    return giver != receiver and (giver not in bad_matches or
                                  receiver not in bad_matches[giver])

# keep trying to generate all matches, stopping if it takes too many iterations
matches = {}
iters = 0
while iters < 10 and len(matches) < len(people):
    iters += 1

    # create a list of all possible receivers from people, copying to allow for
    # mutation later
    receivers = [p for p in people]

    # find a receiver for each giver
    for giver in people:
        # generate a list of possible receiver for this giver
        valid_receivers = [r for r in receivers if can_match(giver, r)]

        # start over if there are no valid receivers left for this giver
        if len(valid_receivers) == 0:
            break

        # pick a random valid receiver
        receiver = random.choice(valid_receivers)
        matches[giver] = receiver

        # remove the chosen receiver so that each person only receives one gift
        receivers.remove(receiver)

# fail if not able to generate all matches
if len(matches) < len(people):
    print(f'Could not generate valid matches in {iters} iteration(s).')
    exit(1)

# print all matches, with nice formatting
print(f'Valid matches generated in {iters} iteration(s):')
max_giver_len = max([len(p) for p in people])
for giver in matches:
    # pad giver with spaces so all arrows line up
    print(giver + ' ' * (max_giver_len - len(giver)) + ' -> ' + matches[giver])
```

And here's a sample output:

```
Valid matches generated in 1 iteration(s):
Bill     -> Carl
Louise   -> Tom
Tom      -> Bill
Sally    -> Jennifer
Jennifer -> Louise
Carl     -> Sally
```
