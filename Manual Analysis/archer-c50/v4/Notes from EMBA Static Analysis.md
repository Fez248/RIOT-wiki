It discovered a LOT  of things. But now comes the hard part, actually investigating which ones are really exploitable and need to be fixed.

Lets start with what should be easy, but not really.
![[Pasted image 20261003131520.png]]

This are the software components that have been identified to contain vulnerabilities, some of them with POC/exploits.

I am going to start by reading the vulns that have an exploit. So, in case I understand anything, manage to emulate the firmware and happens to be exposed I will have a way to attack it.

A lot of things need to happen as you can see for this to work, but it is fun to try.

Although for Ferrita Security we probably do not need to do all this process of actually exploiting the vulnerability. Just the mere fact of having that vulnerability there, even if not exposed is probably already a reason to be patched. A future update can end up exposing that vulnerability. And checking for each update and for each know vuln if it changed anything can become increasingly complex, to the point where I am sure it would be more intelligent and safer to just patch those vuln when possible.

So, lets start reading [[CVEs with exploits]].