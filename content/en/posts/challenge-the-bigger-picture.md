+++
date = '2025-10-24T20:20:52-07:00'
draft = false
title = 'Challenge the Bigger Picture'
+++

AI is great at helping you work through a problem, but it’s terrible at questioning whether you’re solving the right one. That’s the big gotcha I keep running into. Once you start down a path, it just assumes that’s the right direction and keeps trying to help you go faster. It rarely stops to ask, “Wait, are we sure this approach even makes sense?”

A good example of this happened when I was troubleshooting networking issues inside my virtual machines. The VMs weren’t getting IP addresses, and after poking around, I saw that DHCP packets weren’t making it back. So I pulled in AI for help. We looked at packet traces, checked bridge interfaces, and stared at tcpdump logs together. It was like having a very eager assistant who wanted to help but didn’t realize we were digging in the wrong spot.

## The Real Problem

The real problem wasn’t buried in the packets at all. It was the firewall. I was using UFW on an Arch-based system, which turned out to be the wrong tool for the job. UFW works fine on Ubuntu, but it’s not meant for Arch. AI never questioned that choice. It just kept feeding me commands and troubleshooting steps as if the setup itself was fine.

At some point, my gut kicked in. Something didn’t feel right, so I stepped back and asked a different question: “What’s the recommended firewall for Arch?” That’s when I found out I should be using firewalld instead. I installed it, and suddenly everything worked. Virt-manager had already set up the right firewalld rules for virtual machines, so once I switched, the problem just disappeared. I’d wasted hours chasing ghosts when the answer was basically, “you’re using the wrong tool.”

## The Lesson

That experience was a good reminder that AI doesn’t really zoom out. It’s great at digging deeper into the thing you tell it to, but it rarely challenges the bigger picture. Sometimes the right move isn’t to keep debugging. It’s to stop, back up, and ask if you’re even doing it the right way. AI won’t do that for you. That’s still on us.
