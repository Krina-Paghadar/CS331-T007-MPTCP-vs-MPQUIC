# Krina — AI Usage Log

**Project:** MPTCP vs MP-QUIC: A Comparative Study of Multipath Transport Protocols  
**Team ID:** T007  
**Member:** Krina Paghadar (24110169)  
**Repository:** https://github.com/Krina-Paghadar/CS331-T007-MPTCP-vs-MPQUIC

This file contains the raw, unedited AI conversations and prompts used during the project, organised by tool: ChatGPT, Claude, and Antigravity. The conversation text is reproduced exactly as exported, without summarising or cleaning up.

---

# ChatGPT

_Raw export of the ChatGPT conversation, reproduced in full below._

# Multipath Networking Research Review

**User:** Anonymous  
**Created:** 10/17/2026 14:34:44  
**Updated:** 11/6/2026 3:01:47  
**Exported:** 11/6/2026 3:25:22  
**Link:** [https://chatgpt.com/g/g-p-6adb348b46c88191920f931e2f9b31b8-cn-project/c/6ad33a2b-975c-83ee-81d5-419e8341aa0f](https://chatgpt.com/g/g-p-6adb348b46c88191920f931e2f9b31b8-cn-project/c/6ad33a2b-975c-83ee-81d5-419e8341aa0f)  

## Prompt:
17/10/2026, 14:40:15

CN sameer meeting - Transcript
--------------------
Speaker 1 | 00:00:03
Not exactly, actually, but it's trying to solve this this problem only.
--------------------
Speaker 1 | 00:00:16
The situation。
--------------------
Speaker 2 | 00:00:17
What I could understand was key on like newer devices. There are multiple parts we can connect through. Like suppose we can connect through WiFi. We can connect through internet.
--------------------
Speaker 2 | 00:00:29
And it's not like if I losewi-fi I don't want that my whole connection is lost that's why we can create multiple paths one through,wi-fi one through internet this, this was the. Problem multipurpose kind of circuits.
--------------------
Speaker 3 | 00:00:44
So the existence of. Devices with multiple interfaces or multiple means to connect to the network has become a norm yes since twenty years. This, is what you. Will see because you will havewi-fi you will have in mobile you,
--------------------
Speaker 3 | 00:01:01
will have so many of, the means to connect so when you have such things. Are you utilizing them better are, you only able to utilize? Them better this multipath mechanism essentially allows you?
--------------------
Speaker 3 | 00:01:16
To do that before I ask you understand the. Background what are the things that were. DoneBefore multiplyPct.
--------------------
Speaker 3 | 00:01:27
There was no aspect going here because so that means first thing that is important is to understand the context of the problem.
--------------------
Speaker 3 | 00:01:38
So context cannot be built just by reading about emphasis. So when you read nptcp, it refers to certain papers and you don't have to read all nptcp. Just the introduction is sufficient to give you.
--------------------
Speaker 3 | 00:01:53
So when you read, you understand, okay, what are all the things that people have done? Why empty so easily in turkish? But and ttcp is outdated. Not only it is still there, but now TCP is getting replaced by two.
--------------------
Speaker 3 | 00:02:11
And the whole project. That's why I gave you was to understand nptcp to understand npg, what are their operational challenges? Because nptcp was introduced twenty years back, but it has not become prevalent. Why?
--------------------
Speaker 3 | 00:02:29
What are the inherent challenges that are stopping it from adopting ncdcp as linuxKernel? Also like in the last two, three years they started supporting the release forMptcp.
--------------------
Speaker 3 | 00:02:46
But still applications are not going towards simplicity. That is where understanding of, okay, what is needed, the kernel point of view, the supporting point, what is needed from the application point of view to utilize NPC?
--------------------
Speaker 3 | 00:02:59
Is it completely agnostic? What are the challenges that are being faced? This is the kind of understanding that you should derive first. Otherwise, what will you speak of interview?
--------------------
Speaker 3 | 00:03:10
I got this result by comparing with this type everyone by unicorn.
--------------------
Speaker 3 | 00:03:16
So that you understand the basic principles of why, how things are working and what is it? Actually。
--------------------
Speaker 3 | 00:03:25
I want you to open your evaluation and say, okay, your evaluation will also make sense at that point because you will be able to justify those results yourselves. And is it that, okay? There is only one nptcp.
--------------------
Speaker 3 | 00:03:39
There are variants of nptcp implementations that are available. So what nptcp variant are you considering becomes important thing? That means one of the project that I had earlier was just compare variance of npcp.
--------------------
Speaker 3 | 00:03:55
Now this time I introduced quick so that you learn about, okay, npk standards that are getting set, it is not yet final complete. Which standards are getting set in different context of how to use.
--------------------
Speaker 3 | 00:04:07
And that is a means to understand, okay, what ah rfc is this setting? Which is compl

See in this speaker 3 is our professor sameer sir and he was explaining about that elrohect his expectations and all so in the second half we are working on this same project again but he wants us to understand the project and not just uk see what claude says and just agree and ratofy, see this time we don't want to loose marks at all
Looking at speaker 3s expectations please tell me what he wants us to do 
The project was :
Project Description: Study and compare MP-QUIC and MPTCP protocols for applications like video streaming, file transfer, and VoIP, focusing on throughput, latency, and connection stability.

Tools/Technologies:
QUIC implementation: quic-go, Cloudflare’s quiche
MPTCP: Linux kernel MPTCP, Multipath-enabled iproute2
Network emulation: NetEm, Mininet
Monitoring: iperf3, Wireshark

Expected Outcomes:
Measure throughput, latency, and reliability under different network conditions
Analyze how each protocol handles packet loss and congestion
Gain practical experience configuring multipath protocols
Provide recommendations for protocol use based on application needs

This we did this in the first half but couldn't complete it to the expectations of sir cause we weren't aware of what exactly are we supposed to present and know 
And this is what we understood last time we did:
[01/09, 2:02 pm] Swamini: What I understood is that it is basically about comparing the two multipath protocols that can use multiple network paths simultaneously. We want to see how they perform under different network conditions like in terms of throughput, latency, packet loss, etc etc, so will have to decide those conditions first under which we will experiment.

The protocol leads will  handle setting up nd validating the MPTCP and MP-QUIC implementations nd checking that multiple paths are actually working. After that my role is to run the experiments under the same  network conditions for both protocols. So the overall flow I understand is 1.set up and verify the protocols 2. create controlled network conditions using Mininet/NetEm 3. run the same experiments for both protocols 4.collect measurements nd analyze,compare the results
[01/09, 2:08 pm] Kaushal Rathi: Yes that is what we are doing
[01/09, 2:08 pm] Kaushal Rathi: The actual project is more of like
[01/09, 2:08 pm] Kaushal Rathi: Like this is from sir*
[01/09, 2:08 pm] Kaushal Rathi: He said these are 2 protocols not implemented
[01/09, 2:09 pm] Kaushal Rathi: But we gotta understand and compare
[01/09, 2:09 pm] Kaushal Rathi: On some benchmarks
[01/09, 2:09 pm] Kaushal Rathi: What are the tradeoffs and all
[01/09, 2:09 pm] Kaushal Rathi: Basically it's just theoretical 
Krina and pratik i had talk with sir as i mentioned and he also said about the data fetching from already done benchmarks. So abhi k liye mptcp waala ek hi jan handle karo and i want one to do these 2-3 things 
Get the already performed experiment and data 
There was more work on MPTCP in earlier years but it was dropped i want to know why like the documented part and for both MPTCP and MPQUIC. The data and the experiment as well. Like what they did why they did what were the tradeoffs etc etc.

Sir wants us to know the basics everything so that we understand the implementation part and I mean suppose he asks anything different or tricky from the implementation part we are able to answer not cause we ratofied but we have that knowledge atleast that we are able to answer those questions. 

I will tell u the questions he asked us in our viva for this project in the first half 
First we had to present our presentation till then he was taking a look about everything in our GitHub that we had submitted 
Then he was asking whether there is HOL blocking in MPTCP and MPQUIC yes or no and why like we had to explain if it happens then how it happens , why the need to multipath then asked what framework we used to compare both of these which we didn't have then what commands would u use suppose we want to implement MPTCP in his laptop right now then what would u do. He had many more such questions (what is TMP) but he didn't ask cause we weren't able to answer even basics of his questions which he expects us to know if we did that project and he was disappointed. 

I hope ur getting what we are trying to do this time cause we are gonna do this project again from scratch in this second half

## Prompt:
19/10/2026, 14:42:26

Now see, looking at sirs expectations and the project, i want you to give me the workflow and the work distribution (4 members, Krina, Kaushal, Swamini, Pratik), our final submission in on 4th november, before that they will give us final report guidelines later on just a few days before the submission and then we wil have to present, and during presentation, the prefessor thouroughly checks the github and everything so dont assume that he will by pass some things, no he wont, he explicitly said that he wants us to understand the basics clearly, i hope u understand what he wants from the project

## Prompt:
19/10/2026, 22:38:55

bro listen sir has said its fine if u dont implement everything, but u must understand the basics od whats gng on, obviously one cannot read all the research papers and everything, but atleast have an idea and not just overview but using that knowledge u must be able to answer any kind of question if asked, like as i said sir asked us whether MPTCP and MPQUIC have HOL blocking or not , we must know that and if asked we should be able to explain as well, why needed multipath?, and why mptcp didnt continue rn, this all is covered in the recording of what sir said, so we want a plan in that not something unrealistic but something where we can confidently understand and answer

## Prompt:
23/10/2026, 15:51:46

the second plaan, the condensed one i am trying to follow, im trying my best understand as much as possible, understand the basics, im referring this rfc 8684: [https://www.rfc-editor.org/info/rfc8684/#name-multipath-tcp-in-the-networ](https://www.rfc-editor.org/info/rfc8684/#name-multipath-tcp-in-the-networ)
im trying to read it and follow, but tbh i need visual understanding and so i tried using notebook lm and pasted this link and got the video overview but it is so small just for about 9 minutes and didnt explain in detail nor did i understand it visually from the video cause sometimes to understand and explain someone u urself need to know and understand so that u cna explain and i understand well by visualizing stuffs

[Attachment: mptcp-mpquic-understanding-plan.md]

[Attachment: mptcp-mpquic-plan-condensed.md]

## Prompt:
23/10/2026, 17:32:31

if we simply start an unrelated second TCP connection over cellular, then the application would have to manage both the connections itself, it would have to figure out which chunk of data needs to go to which connection and then track which data arrived and handle duplicates and recover the correct order and also what if the connection fails, and so MPTCP provides a mechanism beneath the application layer that coordinates these subflows on behalf of the application layer and makes it look like one single connection to the application layer

## Prompt:
23/10/2026, 17:41:17

Now to add another subflow to an existing subflow, the client send a SYN + MP_JOIN option to the server along with a token which is made using the clients and the servers key which they shared during the first connection and also an HMAC for authentication, and ig some random nonces are also shared but i dont know much about it, explain it as well, then the server verifies using the token and the HMAC and responds back to the client as SYN-ACK+MP_JOIN, idk if they share something as well, and then the client accepts it and adds it as another subflow by sending ACK+MP_JOIN along with data??

## Prompt:
24/10/2026, 18:15:14

The server won't send the SYN/ACK back to the client if the token does not match maybe, ig HMAC Just authenticates or helps verify once we know it belongs to the same connection, im not sure

## Prompt:
24/10/2026, 18:22:09

Just because the token matched dosen't mean that the server must accept the subflow, token matching says that u want to add to that particular connection, but if HMAC if invalid it says that u don't have relevant information about the client and the servers keys for u to be added to this connection, so ig when the client sends its ACK and the HMAC and when the server tries to verify and it comes out to be invalid, it won't send the final ACK right?

## Prompt:
24/10/2026, 18:27:04

okay let's move further in the story as u said, but before that i have one more doubt, how does the client and the server verify the HMAC?

## Prompt:
24/10/2026, 18:32:09

okay carry on

## Prompt:
24/10/2026, 18:52:47

MPTCP, it preserves one ordered byte stream. So the application would expect an ordered byte stream of the data. So when we are reassembling DSNs, it would have the later data, but the earlier DSNs from 100 to 199 are missing. And since MPTCP, I mean the application, it expects an ordered byte stream, the receiver will buffer the later on data, means the DSNs from 200 to 299. It will buffer the data until and unless we recover the earlier DSNs, which are from 100 to 199. And so this is the head-of-the-line blocking, I mean connection-level head-of-the-line blocking in MPTCP.

## Prompt:
24/10/2026, 23:56:28

Okay, so now suppose Wi‑Fi fails while the DSNs 100 and 199, 100 till 199 are missing, but the cellular is still active and has already delivered the DSNs 200 to 299. Now MPTCP will definitely need to retransmit these 100 to 199 because they are missing and the only other available sub-flow is the cellular one. Okay, if we are considering, I mean if we are assuming that there are only two sub-flows for that particular MPTCP connection. So obviously if you have missed some packets, and since at the end in the application side you will have to, you know, pass the ordered byte stream, you would need those earlier bytes if they are missing just because Wi‑Fi failed, you would have to retransmit through the cellular path. And this is different from retransmitting a lost TCP segment on the original Wi‑Fi sub-flow, because the TCP segments on the Wifi were sent but the connection on that subflow failed and so those segments needed to be retransmitted on cellular??

## Prompt:
25/10/2026, 00:30:48

The receiver would get to know this duplicate with the help of the DSN, two bytes on different subflows can have the same TCP sequence number but they belong to different subflows but they would have their DSN mapped, so when the receiver uses these DSN to order the bytes, it will have two data with the same DSN and it will recognize these duplicates, and it will drop on of it?

## Prompt:
25/10/2026, 00:43:06

okay

## Prompt:
25/10/2026, 10:18:39

So suppose the Wi‑Fi TCP ACK confirms that the bytes on the Wi‑Fi subflow are arrived successfully on the receiver end, but an earlier DSN sent over the cellular is still missing. Then the Wi‑Fi TCP ACK alone doesn't prove that the application received the entire stream, because the earlier data that was sent through the cellular has still not reached the receiver. Since MP-TCP sends the data in an ordered bytes stream at the end before sending it to the application. It would need an earlier data as well. So the Wi‑Fi TCP ACK will not alone prove that the application will receive the entire stream. It has to wait until and unless it recovers the earlier DSNs that were missing on the cellular side.

## Prompt:
26/10/2026, 23:38:15

yeah sure, and i hope we are following the plan that we had made (Krina's part) and are working on it according to the requirements.

## Prompt:
26/10/2026, 23:41:42

yeah, and how much time will it take to cover all of these things about my portion with proper confidence for the presentation and the viva

## Prompt:
26/10/2026, 23:56:28

okay let's move to the next topic then

## Prompt:
27/10/2026, 18:32:43

My answer to the MPTCP path-management viva question: B. My reasoning: ADD_ADDR only tells the my laptop that this address is available and u can check if wanna add a subflow, it dosen't guarantee that the subflow will be established or not
. Please evaluate my understanding and correct me if needed.

## Prompt:
27/10/2026, 18:35:50

I don't think marking cellular as backup means that MPTCP can never send data over cellular while Wifi is working. Both the subflows are established on my laptop but ig its still not guaranteed that the data will move from both the subflows, and marking as a backup means that cellular is a usable establsihed subflow over which data can be sent...this is my understanding

## Prompt:
27/10/2026, 18:41:27

One can have multiple subflows in a connection and still distribute data differently across these paths, ig distribution of data depends on the path bandwidth, latency and many more metrics, and according to that MPTCP decides which data to assign on which path

## Prompt:
27/10/2026, 19:09:34

if the scheduler sends all the data over Wifi then it can becomes congested at some point and it will have to send data over cellular since it would not stop sending data casue of traffic cause it has alternate available

## Prompt:
27/10/2026, 19:14:36

It will keep those bytes in the receiver buffer cause at the end the application needs the data in order, and since the initial bytes are missing, so the receiver waits until and unless these initial bytes are recovered

## Prompt:
27/10/2026, 23:01:25

since MPTCP preserves a single ordered byte stream across the subflows, so the application cannot consume the bytes beyond the gap until and unless the earlier missing bytes are recovered, and so a missing byte on one path can elay the application deliver of bytes that has already arrived over the other path. Altho, the application will continue to deliver the bytes that arrived before the missing byte

## Prompt:
28/10/2026, 00:24:14

in QUIC, the application need not wait for stream As missing data before receiving data from stream B, stream B can progress independently, cause quic supports multiple independent streams within a connection
now my question is what is the difference between supporting multiple streams and multiple subflows within a connection?

## Prompt:
28/10/2026, 00:29:47

My answer to the QUIC streams versus paths question is b. Please evaluate it and continue the tutorial.

## Prompt:
28/10/2026, 10:56:46

My MP-QUIC HOL blocking answer is b. My reasoning: QUIC has multiple streams and so they work independently
. Evaluate it and continue the CN project tutorial.

## Prompt:
28/10/2026, 23:03:16

Now suppose we have, as you said, flow A, which is an ordinary TCP flow, and we have flow B, which is one MPLS TCP connection with two sub-flows in it, and as given to us that the MPLS sub-flows, they are independent, so they don't have any coupled congestion control. So suppose both of the users, flow A and flow B, they share a bottleneck in between, right? So now since user B has two sub-flows in it, both of them, and since each of them are independent TCP flows, so as compared to user A, the user B will compete for, I mean, it will effectively have two congestion-controlled flows competing for the capacity, the bottleneck that user A is also using, right? And that is why user B will have a disproportionate share of the bottleneck bandwidth, and so it will have more bandwidth. I mean, I'm still not understanding how will I explain, because these words are a bit, you know, confusing. I mean, I just don't understand the way you use the word of congestion and, you know, shared bottleneck and disproportionate. I just don't understand these words. I want to understand this thing, you know, easily, but to the point and correct. Not just, you know, something superficial. No, not at all. I'm understanding the basics, as I have told you.

## Prompt:
02/11/2026, 22:41:17

bro i want to make a quick detour before we move on please

we will have to make github repo man naming: [**CS331-T007-MPTCP-vs-MPQUIC**](https://github.com/Pratik-Kumar-Dhakar/CS331-T007-MPTCP-vs-MPQUIC)  (this is previous repo forget this) but name must be like this there are certain requirements bro and what should our repo have man i mean we dont even have any code there all we did is just wokr according to the md file that we had made earlier , but see it must be systematic enough cause sir checks each and every thing tagged in there proper structured and also what FRAMEWORK we used on which we are comparing these both and everything that i told you sir expects us to know cause we are just understnading these two and we have not implemented ourselves or should we look at other implementations done till now but its like sir expects us to know how they were implemented but he is also not saying its fine if u dont implement but atleast have a knowledge about what u have done and then he still asks that what is implemented for mptcp till now and also its not into work yet then why was it even taken picture into that mptpc must be there while its still not handy and workable and all that and he asked me that u must know the commands and all i mean what if i want to enable mptcp in my laptop right now what will u do, ig all these things needs to be done so help me setup the github i have submission on 4th november or else give me the proper to the point prompt for antigravity cause it can help me setup the github for me with all the details please with me as the owner and i want to allow my teammates to push and all in it as well whenever they especially their ai usage cause they have to contributers na, now i am sending u their requirements:

Hi all,\
All project deliverables; code, report, and presentation slides ; will be submitted via GitHub.\
Repository setup:\
One GitHub repository per team, named: CS331-\<TeamID>-\<ProjectShortName> (e.g., CS331-T001-BandwidthTracker)\
Include a short README.md at the root with: Team ID, Project ID, Project Title, and all team members' names + roll numbers\
Folder structure (required):\
&#x20;\
&#x20;\
Plain Text\
README.md\
/code       → all source code\
/report     → final report (PDF)\
/ppt        → presentation slides (PDF or .pptx)\
&#x20;\
Deadline:\
Once your team is ready to present, book your evaluation slot with your TA.\
Your repository must be fully updated. Code, report, and slides at least 24 hours before your scheduled slot.\
We check the GitHub commit timestamp, not when you tell us it's done. Commits after that window will be treated as a late submission.\
2026-27 Sem 1 CS 331 - Computer Networks

this was our readme last time:

# CS331-T007-MPQUICvsMPTCP

**Team ID:** T007

**Project ID:** CS331-T007-MPQUICvsMPTCP

**Project Title:** MPTCP vs MP-QUIC, A Comparative Study of Multipath Transport Protocols

## Team Members

| **Name**            | **Roll Number** |
| ------------------- | --------------- |
| Kaushal Rathi       | 24110290        |
| Krina Paghadar      | 24110169        |
| Pratik Kumar Dhakar | 24110277        |
| Swamini More        | 24110211        |

## Repository Structure
```
README.md
/code    - all source code, scripts, and experiment logs
/report  - final report (PDF)
/ppt     - presentation slides

```

## Other Contents

- `/AI_Used` - AI usage documentation, as required by the course announcement.

Project Submission: Deadline & AI Usage\
Reminder for the deadline & To update you Github repos for AI use Documentation\
Hi all,\
Additionally, every team must document AI usage in their GitHub repository for the teams who submitted & not yet submitted:\
If your team used AI tools, add a folder named AI_Used\
If your team did not use AI tools, add a folder named AI_Not_Used\
The AI_Used folder should contain:\
Tools – which AI tools were used\
Prompts – the prompts given\
Thought process – how AI was integrated into your workflow\
Step-by-step details – where and how AI contributed at each stage\
Please ensure your repository is updated before the deadline.\
Thanks\
&#x20;\
2026-27 Sem 1 CS 331 - Computer Networks

i have rn shared all my prompts that i used for project from chatgpt and claude till today excluding the one im writing rn

AI Usage\
Hi all,\
&#x20;\
Update your GitHub repos with the prompts you used across all AI Platforms for your project.\
&#x20;\
Share the raw prompts; there is no need to "summarise" the conversation or "clean up" the conversation.\
Collect the entirety of your conversation and copy-paste it into a single markdown file and place it in the AI_Used folder in your Project's GitHub repo. \
&#x20;\
You may use the Print/Save to PDF option available in the browser.\
&#x20;\
AI_Used folder should contain every prompt/conversation you had with AI regarding the Project.\
&#x20;\
There will be negative marking if prompts are not honestly submitted.\
&#x20;\
Please ensure your repository is updated before the deadline.\
Thanks\
&#x20;\
2026-27 Sem 1 CS 331 - Computer Networks

my githun uk already Krina-Paghadar

[Attachment: mptcp-mpquic-plan-condensed(1).md]

## Prompt:
02/11/2026, 23:00:52

bro we would aslso need to make ppt man which needs to added in the ppt thing and not only readme bro and also framework mean sir said under what conditions did u check both the frameworks that is necessary for us to comapre two protocols like bandwidth and all and how many paths are we considering and all and congestion and everything i hope u understood, and rn we have just read the documentation and tried understanding both the protocols and ig we need to have a look on what all is implemented till now cause even ppt has to have a flow and must be simething real and not fake that we cant defend and ig i must do today some work on coding part , i have not configured myself and checked which i think i need to in my laptop broan di myself will add them as collaborators

## Prompt:
02/11/2026, 23:30:15

bro lets us not give evrything at once to antigravity bro and we need to give exactly what we have so that we only have those things on github in a systematic structured way so that the professor can grade properly and understand what exactly we have done in the project and not just did everything last minute and used AI and made and rememebred the ppt and then just explained there, u can guide me to setup and all so that i can explain it there if he asks and atleast we will have somethings to show but dont exaggerate its fine if we have done under simple conditions but whatevr we did must be understandable by us no need to make it long enough and all its fine but i must own what i did, i will understand and configure and learn from it in my laptop, i use windows btw and i have wsl

## Prompt:
05/11/2026, 17:33:10

listen forget this now cause we literally didnt code anything or checked anything in my laptop, all we did is that we all four worked according to the condensed plan that we had shared in the start, so we just understood overall about mptcp and mpquic right so now we want to make the github repo and think what all to add in it , format i have shared earlier already and make report and ppt proeprly 
so now tell me what to add, or else whatevr i have done till now in my (Krina) part tell me that once so that i can let CLAUDE PRO know and then it can thin and let us know what to do and how to structure the repo which would be easier for the profesor to udnerstand our work

## Prompt:
06/11/2026, 01:26:51

Okay. So listen, what I am thinking right now is you know exactly what I have studied, right? According to my part, obviously from the condensed MD file that we had planned in the starting, that according to that we'll all will work upon. So you know my part, right? We both studied together in detail and discussed every topic that was under my part, Krina, okay? So from that, you tell me what all I have covered. Be honest, okay? It's not compulsory to add everything that had been planned in the condensed MD file, okay? Even though I have not done it, I will only include the contribution of me that I have exactly done, okay, till the date. And also, as of now, consider that Kaushal, Swamini, and Pratik also have done 60 to 70% of their given part from the condensed MD file, okay? And also, yeah, this, and one more thing, from the report, I want to understand what the AI part is, like what is being said about the AI part, what all needs to be included, and then give me a prompt for Claude, please. Exactly what needs to be done, as I just conveyed to you, okay? And I have the report made up now, but it is not as I expected, okay? So I want a little— it's too much, you know, depth, and too much is written in it, given by Antigravity. So I want it to be updated according to the template given to us, okay? And nothing extra to be added. It's too much exaggerated, too much of things written, okay?

## Prompt:
06/11/2026, 01:29:10

her eis the template and the the report given by antigravity, obviously we didnt read all the references and uk which refernece i read ig rfc 8684 about mptcp

[Attachment: Final Project Report Template (1).docx]

[Attachment: CS331_T007_Report.pdf]

## Prompt:
06/11/2026, 01:53:51

now it made like this!!!!
how is it ???

[Attachment: CS331_T007_Report_REVISED.pdf]

## Prompt:
06/11/2026, 02:09:56

Okay, so now, whatever the problems you think this report has, which needs to be updated, tell me that in the prompt for Claude. I mean, give me the prompt for Claude. And also, apart from that, about Kaushal, Prateek, and Swamini, I am attaching the zip of Swamini, that the work she, whatever she has done, you can take from there, her work. And Prateek's work, whatever the MD file has mentioned, please add up to 70% of it, okay? And add the RFC, or add the reference that is given in that particular... And it's fine if you don't add his reference also. It's fine. It's not necessary that you read all the references, okay? Obviously you cannot read those many references, and that too in detail. It's fine if you don't even add, okay? Kaushal also it's fine, don't add those many anything, because he genuinely hasn't read any RFC, but he has just used some data. That is fine, we'll tell him, okay? Apart from that, Swamini's work I am adding to you. You know my contribution already, Kaushal's contribution also you write 60 to 70% to his given, according to the plan. Prateek's also up to 60 to 70%, okay? And apart from that, whatever technical points you think must be needed, you can, I guess we will check it later. And references also remove those references, only add some of those, like RFC 864 I read. It's fine if you don't add those, okay? And AI usage needs logs. That I will share you in some.

## Prompt:
06/11/2026, 02:12:34

and in the ai contirbution do we need to adds logs in the report or what???
have atatched swamini zip and she sent her files:
De Coninck and Bonaventure, Multipath QUIC: Design and Evaluation (CoNEXT 2017): https://inl.info.ucl.ac.be/system/files/conext17-deconinck.pdf
De Coninck and Bonaventure, MultipathTester (MNM 2019): https://inl.info.ucl.ac.be/system/files/multipathtester.pdf
so we need to add the links in report or what specidy that to me

[Attachment: MPTCP_MPQUIC_Swamini.zip]

## Prompt:
06/11/2026, 02:14:51

bro tell only the updates needed after the report it made and gave dont write eevrything again the prompt please

## Prompt:
06/11/2026, 02:30:57

bro isnt this too weird and too much??? and they have writtena  lot of findings or is it swaminisss is it necessary to be added

[Attachment: MP-QUIC_vs_MPTCP_Final_Project_Report (1).docx]

## Prompt:
06/11/2026, 02:48:57

and now u have to make the ppt please, format is this:
Everyone should follow this Presentation Structure. For Those teams who have already submitted create a different ppt file & upload dont edit the exsting one.
 
Slide structure (5 slides):  May extend one slide
Problem Statement & Objectives
Architecture / Mechanism — your design and how it works
Extension / Issues Fixed / Evaluation — what you built on top, bugs resolved, and results
Non-Functional Testing Parameters — performance, scalability, reliability, etc.
Challenges Faced

and yeah content uk what to follow as we said, only whatevr we have done keep the template simple adn clear 

i have shared the docx given by claude now for the report okay check it once now i want to give it prompt for ppt and format is above, give me the prompt for claude

[Attachment: MP-QUIC_vs_MPTCP_Final_Project_Report_v3.docx]



---
Powered by [ChatGPT Exporter](https://www.chatgptexporter.com)

---

# Claude

_Raw export of the Claude conversation, reproduced in full below._

# CN course project PHASE II

**Created:** 10/21/2026 16:26  
**Updated:** 11/06/2026 02:54  
**Exported:** 11/06/2026 03:25  
**Link:** [https://claude.ai/chat/409161c5-8709-4479-a32c-aa8fa314b099](https://claude.ai/chat/409161c5-8709-4479-a32c-aa8fa314b099)  

## User:
10/21/2026 16:26

this is the plan that we had made roughly for our course project, but we dont have much time, we have maybe roughly 3-4 days and 13 hours per person, cause we won;t be obviously working on this daily depending on the timeline given, so it's like whichever days we have time we will give this time, altho sir has told that u would need to atleast give half an hour to understand the basics rather than memorising just a few days before the submission, so now given the real life scenario of us, can u reorder the plan for us please, cause realistically we won't be able to give time daily dedicatedly into this.


## User:
10/21/2026 16:31

give me the md file of the reordered plan please so that i can share with my teammates, i would like to give u the amount of work each person from my team would be able to do from highest to lowest: Kaushal, pratik, krina, swamini
Altho its fine, we all we try to manage and coordinate as much as we can apart from the amount of work we would be able to do, but the aim is to have a good understanding of the project with confidence


## User:
10/21/2026 21:35

okay so I'm Krina, lets start working on my part then, i have time right now


## User:
10/21/2026 22:37

https://www.rfc-editor.org/info/rfc8684/

okay so i have opened this and read the starting part of it, ig this contains the MPTCP v1, first it says that we usually have multiple paths between peers just like we have wifi and cellular, so usage of multiple paths improves recource usage within the network and can also improve user experience via higher throughput and improved resilience to network failure. (One question arrives to me that will mutlipath always improve throughput?), then this RFC contains the extension of TCP and not a completely new protocol itself for multipath, i think this is cause middleboxes understand TCP  and UDP so middleboxes might face a problem for understanding MPTCP if we make it a new protocol, so we extended TCP itself, wherein we stuffed the multipath details in TCP options

So means this extension provides the same type of service as TCP and also have some components necessary to establish multipath.
So the protocol changes to add multipath capability requires quite a lot of stuff: signaling, setting up multiple paths (subflows), managing these subflows, reassembly of subflows, termination of sessions, ATLHO these are NOT THE ONLY changes required.( what are some other changes? might be asked)

MAIN DESIGN ASSUMPTIONS:
1) must be backward compatible with TCP, so that it is easier to deploy
2) assumed that one or both the hosts are multiaddressed (maybe assumed that multipaths can exist?)

These paths need not be entirely disjoint: they may share one or many routers between them. Even in such a situation, making use of multiple paths is beneficial, improving resource utilization and resilience to a subset of node failures. The congestion control algorithm defined in [[RFC6356](https://www.rfc-editor.org/info/rfc8684/#RFC6356)] ensures that the use of multiple paths does not act detrimentally. Furthermore, there may be some scenarios where different TCP ports on a single host can provide disjoint paths (such as through certain Equal-Cost Multipath (ECMP) implementations [[RFC2992](https://www.rfc-editor.org/info/rfc8684/#RFC2992)]), and so the MPTCP design also supports the use of ports in path identifiers.
(i didn't get this part, i reached here btw)


## User:
11/05/2026 17:41

> File: Krina AI usage_.docx

> File: Final Project Report Template 1.docx

umm we have not implemented anything nor have we coded anything we have just read and if u think this isnt much for this project then we still have time to do something meaningful that we can defend cause sir said that we must know how rn MPTPC and MPQUIC has been implemented and know why isn't it being used now and all those tricky queestion, at the end we don't want anything fake in the repo such that we cannot defend in front of the professor, final project template is shared and must be used as it is, ppt also realisitic and in a flow that we have wooked on


## User:
11/05/2026 17:48

bro submission is tomorrow:
Hi all ,
2026-27 Sem 1 CS 331 - Computer Networks,
 
Deadline extended: The Project 2 deadline has been extended from 4th November to Friday, 6th November, 10:00 AM.
 
Submission (same as before): All deliverables (code, report, presentation slides, and AI logs) are submitted via GitHub.
 
Late submissions: We check the GitHub commit timestamp. If you need more time, you may submit after Friday 10:00 AM, but commits after the deadline will incur a 5% penalty on Project 2.
AI logs we all will try and update it in github then before tomorrow morning

now accordingly tell me what to do


## User:
11/05/2026 17:50

is it possible to do in my laptop? im currently using windows but u tell me to setup linux in here properly in the given time frame, i have wsl already in my laptop


## User:
11/05/2026 18:00

![1793881777979_image.png](data:image/jpeg;base64,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kz/zLOYq/UpyPRKgppb3Bca+RslvgbMx0MesCHFuCd/H0sY6edck5o2hawktzgHCk4tIa+Ktqappi16qPZSsMTTG5oxgauMcw7FqtuM4pZ6cCMRTyCRwDBnIzjB5hv4K001x5mSIqh1U30etjDAy5h8jnY1TCQBh7Wu355tcfNajdFKBl0oo3XB81LNVupJHMi1XB7SAQMngc8fktel0yuQuNPLVy68LJNZ7WsAJBc1zsfiwLBddJ6y43Bs0bmQxw1D54RGwMw4uzrHHE7h2LVFN7OJlhi56ZZnWG3OqK+RtfKyhonBr5HQ5frFxaAG538OKzWvRKnuUUbm3NoNTVOpafERIkcACCegHK0RpNXiplm1aU7YASM2DdR+DkEtxjOedbkOmNVSWdsVOI21xqpKgymJpDNZoALeg7jwVmLsR4kmK8eHObJ22EQ+0Xav45wuxrvo8qKKopIn1bQZqhtO8uZgBxGct35cOxct5RqBb+RAs2O12+dQa2tjH2uOPYpCXSm5zTQzudCJopBKJGwtDnuAwC443nCzri7ONPhlOqfRvx6HMqKqjFNWyT09VHJI17ICXgsdqkaucceckBbLNEaKnhuNJX1WyqIKuCCOZrC7841xwW592eOMKEp9JblTQMgY+J8LGOj2ckTXNLXO1iCOffvWdumV4bPLMX073SuY9wfTsI1mAhpxjiMrXNF6fGWOLkssltp4NG7vFNSxCtttWyHlDHOy7LnAjBOMej0LaqtAammtcFS6obtJTD6JGG/lSA3BzkkawzuUUzSW4NoaqlOweyreZJnPha5z3ZJzkjOck9qtm0juM9PFE98WYwwCURNEpDMauXcd2B2LLTdz4XFaRvtkt9s0chkppuUVArpaeSUtLPstb6OM4xkk59q5nmUpddIa+707IKowiJsjpg2OJrMvcAHOOOJOAovmWy3FUR/0zpiceRERbWQiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICo/gFVUfwCCxERAREQEREBERAREQEREBERAREQEREBERAREQEREGwiKS0eoBdNJLfQue2MVE7Gazm6wGTzjn9yDKzRW/SUYq2WmqdTlm0EgjONXjlROF6bNpjo1TSyQPoKbMRLCPIkHNu9dcbpfQMtelNVTRuYWnVk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+W0/XM7VTllN17O1avmzX+vD3j4J5s13rw94+CbS9xNpe4y2uWU3Xs7VXltP1zO1anmzXevD3j4J5tV/rw94+CbS9xNpe4y2uWU3Xs7U5ZTdeztWr5s13rw94+CebNd68PePgm0vcTa3uMtvltP1zO1U5ZTdeztWr5tV/rw94+CebNd68PePgm0vcTaXuMtrllN17O1V5bT9cztWp5s13rw94+CebNf68PePgm0vcTaXuMtvllP17O1U5ZTdeztWr5s13rw94+CebNd68PePgm0vcTa3uMtvllN17O1OW0/XM7VqebNd68PePgnm1X+vD3j4JtL3E2l7jLa5bTdeztTllN17O1avmzXevD3j4J5s13rw94+CbS9xNpe4y2+W0/XM7VTllN17O1avm1X+vD3j4J5s13rw94+CbS9xNpe4y2uWU3Xs7VXltP1zO1anmzXevD3j4J5tV/rw94+CbS9xNpe4y2+WU3Xs7VTllN17O1avmzXevD3j4J5s13rw94+CbS9xNre4y2+W0/Xs7U5bT9cztWp5s13rw94+CebNf68PePgm0vcTa3uMtrllN17O1OWU3Xs7Vq+bNd68PePgnmzXevD3j4JtL3E2l7jLb5bT9cztVOWU3Xs7Vq+bVf68PePgnmzXevD3j4JtL3E2l7jLa5ZTdeztVeW0/XM7VqebNd68PePgnm1X+vD3j4JtL3E2l7jLa5ZTdeztTllN17O1avmzXevD3j4J5s13rw94+CbS9xNpe4y2+WU/Xs7U5bT9cztWp5s13rw94+CebNd68PePgm0vcZNre4y2uWU3Xs7U5ZTdeztWr5s13rw94+CebNd68PePgm0vcTaXuMtvltP1zO1U5ZTdeztWr5tV/rw94+CebNd68PePgm0vcTaXuMtrllN17O1V5bT9cztWp5s13rw94+CebVf68PePgm0vcTa3uMtrltN17O1OWU3Xs7Vq+bNd68PePgnmzXevD3j4JtL3E2l7jLb5bT9cztTllP17O1anmzX+vD3j4J5s13rw94+CbS9xk2t7jLa5ZTdeztVeWU3Xs7VqebNd68PePgnmzXevD3j4JtL3E2l7jLb5bT9cztVOWU3Xs7Vq+bVf68PePgnmzXevD3j4JtL3E2l7jLa5bTdeztVeW0/XM7VqebNd68PePgnm1X+vD3j4JtL3E2t7jLa5ZTde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5ud3EFByOqmquw80KCfSEWWmq7hHVvMrIzV0rY2SSNB1WtIcftEY/FQk1ldS6LxXWok2ctRUOhhgI3kMHpOPuJA7UEVhUTJKICIiChKtJVxVpQY3cVhf+kR++3/ZZncVif8ApEfvt/2WVH5Qyp/KHcgbldlWjgFVexj9PZQZVcqiLJVc+xUz7ERQEyiKhlERAREQMoiICIiAiIgIiIZERFAREVBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQc1pT+eg/dP81ALoNKfz0H7p/mufXlut9+p5brffqZIPz7PeswKxU++oZ71kbwXG42QKqoFVAREQEREBERAREQEREGwpLR6vbatJLfXvJDKadkjiBk6ocM/LKjUQdPXWS0VN0qZotJbY2nllc5oe2UODSc7wGdBWnpdc6e76V1lVSPL6UkMhcRjLGgNG78FCKo4oOjsumFZYrbS01GHNdBW8qc4PIEgLdUsI6MLfZp3SwiGaO1OFZQxTwUTzPlkcchcfSGPSLdd2OHtXHZCocFB2cWnlJTVArqe1yNr3Qw00j3T5YWRlu8DG5x1QOgKj9PaeWqFfLbHur4ROyneJsMa2VzidZuN5GuccPauMwmEHSaRaWx6Q26kozb2UzbfiOlLXlxZFqgFrs/aORnPtKyVmmU89NKynhdSzOFLqSsk9JhgaQCN3Px9i5dXZCDqLnptJc9KbTe5aKOOSgbGHxxnDZC1xJPDdklXjTOjo5Xm1Wl9OKmrZVVTpajaOl1H64YDqgNGd/BcpuVqDor1pDT19wjuFFBX01YycztfNWbZrTnPojVGN6w6VaRv0luTKkUzaSKOPUZCxxLWkkucfxcSVBogIiICIiChVpVxVpQY3LFJ+kh+83/ZZXlYpP0kP3m/7LKj8oZU/lDuRwCqqDgFVeyh7IRERRERUEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERAREQ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CCYq6qGho5amokEcMTS57zwACirLpfZ77bTWU1U0Njj2srHHfE3pPYpojWaRnGRhc9YbffbLaXW90dumZTsIpniZ7S/0iRrjV9HcebKDPQaS0lRZ5LnVTU0FIJ3RMlbLrscNbVac43E9C2ItIrPNRz1bLnTOp6cAyyB41WAjIyfaucj0Yv8APZqmhqzbozJcGVzHRTPd/wCsHuacsHMN3t6Fot+ju5+THwmtgZO0Uro3Me8AviJJBOAQDncRvQd3Q3CkudK2poamOpgdkB8ZyMjiFsqAstor7VZa7UbTtudTI6bL6iSeN0mqAC5zgHcwzgcynIBLyePb6m21Rr6mdXWxvxnmygvXNacfoy2f+70X/faulXNacfoy2f8Au9F/32oPAfpm/wDNO5+6L/QFZZv0PT+4/wAyr/pm/wDNO5+6L/QFZZv0PT+4/wAyvqfS/dn/AB9X6Z7s/wCN5ERehegEREBERAREQEREHNaU/noP3T/NQC6DSn89B+6f5rn15brffqeW6336mWn/AMQz3q5itp/8Qz3q5i43GyhXBWhXBAREQEREBERAREQEREGwiIgIiICIiAiIgIiICIiAiIgIiICIiChVhV5VhQYn8VY/9Ij99v8AsrnHerH/AKRH77f9llR+UMqfyh3Q4BVVBwCqvZQ9kIiIoiIqCIiAiIgL1m0/ojQb/rSf9qReTL1m0/ojQb/rSf8AakXyfqntx/r5X1P24/136Ii+A8+IiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiIgIiICIiAiJjdlARMIdyAiqWkHBGD7VTnIIwUBEwmEBERAREQEREBERAREQEREBERAREQEREBERAREQEREBERBQNAzgAZOThVREBERAREQEREBERAREQEREBERAREQEREBERAXNacfoy2f+70X/AH2rpVzWnH6Mtn/u9F/32oPAfpm/807n7o/9AVlm/Q9P7j/Mq/6Zv/NO5+6P/QFZZv0PT+4/zK+p9L92f8fV+me5P+N5ERehegEREBERAREQEREHNaU/noP3T/NQC6DSn89B+6f5rn15brffqeV6336mWn/xDPermK2n/wASz3q5i43IyhXBWhXBAREQEREBERAREQEREGwiKQsT4Y7/AETqgtEO1GuXcMe1BHouwbbaOlsz6e4siMzHz1LGNlaC4Bo1fSaTuJ5lng0a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)

wsl: Invalid escaped character: 'p' in C:\Users\Krina Paghadar\.wslconfig:2
Welcome to Ubuntu 24.04.3 LTS (GNU/Linux 6.18.54.1-microsoft-standard-WSL2 x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/pro

 System information as of Thu Nov  5 15:28:16 +03 2026

  System load:  1.1                 Processes:             67
  Usage of /:   1.5% of 1006.85GB   Users logged in:       0
  Memory usage: 6%                  IPv4 address for eth0: 172.21.61.205
  Swap usage:   0%

  => /usr/lib/linux-tools/6.18.54.1-microsoft-standard-WSL2 is using 100.0% of
     96MB

 * Canonical Workshop gives developers fast, composable, reproducible, and
   secure developer environments that are perfect for agentic workflows.

   https://ubuntu.com/workshop

This message is shown once a day. To disable it please create the
/home/krina_paghadar/.hushlogin file.
krina_paghadar@Krina:~$ uname -r
6.18.54.1-microsoft-standard-WSL2
krina_paghadar@Krina:~$ sudo apt update && sudo apt install -y iproute2 iperf3 mptcpize tshark
[sudo] password for krina_paghadar:
Get:1 http://security.ubuntu.com/ubuntu noble-security InRelease [126 kB]
Hit:2 http://archive.ubuntu.com/ubuntu noble InRelease
Get:3 http://archive.ubuntu.com/ubuntu noble-updates InRelease [126 kB]
Get:4 http://security.ubuntu.com/ubuntu noble-security/main amd64 Packages [1157 kB]
Get:5 http://security.ubuntu.com/ubuntu noble-security/main Translation-en [233 kB]
Get:6 http://archive.ubuntu.com/ubuntu noble-backports InRelease [126 kB]
Get:7 http://security.ubuntu.com/ubuntu noble-security/main amd64 Components [46.4 kB]
Get:8 http://security.ubuntu.com/ubuntu noble-security/universe amd64 Packages [1225 kB]
Get:9 http://security.ubuntu.com/ubuntu noble-security/universe Translation-en [247 kB]
Get:10 http://security.ubuntu.com/ubuntu noble-security/universe amd64 Components [76.3 kB]
Get:11 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 Packages [1408 kB]
Get:12 http://archive.ubuntu.com/ubuntu noble-updates/main Translation-en [311 kB]
Get:13 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 Components [181 kB]
Get:14 http://archive.ubuntu.com/ubuntu noble-updates/universe amd64 Packages [1708 kB]
Get:15 http://archive.ubuntu.com/ubuntu noble-updates/universe Translation-en [343 kB]
Get:16 http://archive.ubuntu.com/ubuntu noble-updates/universe amd64 Components [388 kB]
Get:17 http://archive.ubuntu.com/ubuntu noble-updates/multiverse amd64 Components [940 B]
Get:18 http://archive.ubuntu.com/ubuntu noble-backports/main amd64 Components [5740 B]
Get:19 http://archive.ubuntu.com/ubuntu noble-backports/universe amd64 Components [12.6 kB]
Fetched 7721 kB in 5s (1539 kB/s)
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
138 packages can be upgraded. Run 'apt list --upgradable' to see them.
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
iproute2 is already the newest version (6.1.0-1ubuntu6.4).
iproute2 set to manually installed.
mptcpize is already the newest version (0.12-4).
The following additional packages will be installed:
  libbcg729-0 libcares2 libiperf0 liblua5.2-0 libmaxminddb0 libnghttp3-3 libnl-genl-3-200 libopencore-amrnb0 libopus0
  libsbc1 libsctp1 libsmi2t64 libsnappy1v5 libspandsp2t64 libspeexdsp1 libssh-gcrypt-4 libwireshark-data
  libwireshark17t64 libwiretap14t64 libwsutil15t64 wireshark-common
Suggested packages:
  mmdb-bin opus-tools lksctp-tools snmp-mibs-downloader geoipupdate geoip-database geoip-database-extra libjs-leaflet
  libjs-leaflet.markercluster wireshark-doc
The following NEW packages will be installed:
  iperf3 libbcg729-0 libcares2 libiperf0 liblua5.2-0 libmaxminddb0 libnghttp3-3 libnl-genl-3-200 libopencore-amrnb0
  libopus0 libsbc1 libsctp1 libsmi2t64 libsnappy1v5 libspandsp2t64 libspeexdsp1 libssh-gcrypt-4 libwireshark-data
  libwireshark17t64 libwiretap14t64 libwsutil15t64 tshark wireshark-common
0 upgraded, 23 newly installed, 0 to remove and 138 not upgraded.
Need to get 26.7 MB of archives.
After this operation, 139 MB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu noble/main amd64 libsctp1 amd64 1.0.19+dfsg-2build1 [9146 B]
Get:2 http://archive.ubuntu.com/ubuntu noble/universe amd64 libiperf0 amd64 3.16-1build2 [87.1 kB]
Get:3 http://archive.ubuntu.com/ubuntu noble/universe amd64 iperf3 amd64 3.16-1build2 [19.0 kB]
Get:4 http://archive.ubuntu.com/ubuntu noble/main amd64 libmaxminddb0 amd64 1.9.1-1build1 [24.4 kB]
Get:5 http://archive.ubuntu.com/ubuntu noble/universe amd64 libbcg729-0 amd64 1.1.1-2build1 [35.3 kB]
Get:6 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 libcares2 amd64 1.27.0-1.0ubuntu1.1 [74.2 kB]
Get:7 http://archive.ubuntu.com/ubuntu noble/universe amd64 liblua5.2-0 amd64 5.2.4-3build2 [123 kB]
Get:8 http://archive.ubuntu.com/ubuntu noble/universe amd64 libnghttp3-3 amd64 0.8.0-2 [59.0 kB]
Get:9 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 libnl-genl-3-200 amd64 3.7.0-0.3build1.1 [12.2 kB]
Get:10 http://archive.ubuntu.com/ubuntu noble/universe amd64 libopencore-amrnb0 amd64 0.1.6-1build1 [98.2 kB]
Get:11 http://archive.ubuntu.com/ubuntu noble/main amd64 libopus0 amd64 1.4-1build1 [208 kB]
Get:12 http://archive.ubuntu.com/ubuntu noble/universe amd64 libsmi2t64 amd64 0.4.8+dfsg2-16.1build1 [112 kB]
Get:13 http://archive.ubuntu.com/ubuntu noble/universe amd64 libspandsp2t64 amd64 0.0.6+dfsg-2.1build1 [311 kB]
Get:14 http://archive.ubuntu.com/ubuntu noble/main amd64 libspeexdsp1 amd64 1.2.1-1ubuntu3 [43.1 kB]
Get:15 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 libssh-gcrypt-4 amd64 0.10.6-2ubuntu0.5 [226 kB]
Get:16 http://archive.ubuntu.com/ubuntu noble/universe amd64 libwireshark-data all 4.2.2-1.1build3 [454 kB]
Get:17 http://archive.ubuntu.com/ubuntu noble/main amd64 libsbc1 amd64 2.0-1build1 [33.9 kB]
Get:18 http://archive.ubuntu.com/ubuntu noble/main amd64 libsnappy1v5 amd64 1.1.10-1build1 [28.6 kB]
Get:19 http://archive.ubuntu.com/ubuntu noble/universe amd64 libwsutil15t64 amd64 4.2.2-1.1build3 [121 kB]
Get:20 http://archive.ubuntu.com/ubuntu noble/universe amd64 libwiretap14t64 amd64 4.2.2-1.1build3 [259 kB]
Get:21 http://archive.ubuntu.com/ubuntu noble/universe amd64 libwireshark17t64 amd64 4.2.2-1.1build3 [23.7 MB]
Get:22 http://archive.ubuntu.com/ubuntu noble/universe amd64 wireshark-common amd64 4.2.2-1.1build3 [587 kB]
Get:23 http://archive.ubuntu.com/ubuntu noble/universe amd64 tshark amd64 4.2.2-1.1build3 [158 kB]
Fetched 26.7 MB in 5s (5113 kB/s)
Preconfiguring packages ...
Failed to stop iperf3.service: Unit iperf3.service not loaded.
Selecting previously unselected package libsctp1:amd64.
(Reading database ... 57291 files and directories currently installed.)
Preparing to unpack .../00-libsctp1_1.0.19+dfsg-2build1_amd64.deb ...
Unpacking libsctp1:amd64 (1.0.19+dfsg-2build1) ...
Selecting previously unselected package libiperf0:amd64.
Preparing to unpack .../01-libiperf0_3.16-1build2_amd64.deb ...
Unpacking libiperf0:amd64 (3.16-1build2) ...
Selecting previously unselected package iperf3.
Preparing to unpack .../02-iperf3_3.16-1build2_amd64.deb ...
Unpacking iperf3 (3.16-1build2) ...
Selecting previously unselected package libmaxminddb0:amd64.
Preparing to unpack .../03-libmaxminddb0_1.9.1-1build1_amd64.deb ...
Unpacking libmaxminddb0:amd64 (1.9.1-1build1) ...
Selecting previously unselected package libbcg729-0:amd64.
Preparing to unpack .../04-libbcg729-0_1.1.1-2build1_amd64.deb ...
Unpacking libbcg729-0:amd64 (1.1.1-2build1) ...
Selecting previously unselected package libcares2:amd64.
Preparing to unpack .../05-libcares2_1.27.0-1.0ubuntu1.1_amd64.deb ...
Unpacking libcares2:amd64 (1.27.0-1.0ubuntu1.1) ...
Selecting previously unselected package liblua5.2-0:amd64.
Preparing to unpack .../06-liblua5.2-0_5.2.4-3build2_amd64.deb ...
Unpacking liblua5.2-0:amd64 (5.2.4-3build2) ...
Selecting previously unselected package libnghttp3-3:amd64.
Preparing to unpack .../07-libnghttp3-3_0.8.0-2_amd64.deb ...
Unpacking libnghttp3-3:amd64 (0.8.0-2) ...
Selecting previously unselected package libnl-genl-3-200:amd64.
Preparing to unpack .../08-libnl-genl-3-200_3.7.0-0.3build1.1_amd64.deb ...
Unpacking libnl-genl-3-200:amd64 (3.7.0-0.3build1.1) ...
Selecting previously unselected package libopencore-amrnb0:amd64.
Preparing to unpack .../09-libopencore-amrnb0_0.1.6-1build1_amd64.deb ...
Unpacking libopencore-amrnb0:amd64 (0.1.6-1build1) ...
Selecting previously unselected package libopus0:amd64.
Preparing to unpack .../10-libopus0_1.4-1build1_amd64.deb ...
Unpacking libopus0:amd64 (1.4-1build1) ...
Selecting previously unselected package libsmi2t64:amd64.
Preparing to unpack .../11-libsmi2t64_0.4.8+dfsg2-16.1build1_amd64.deb ...
Unpacking libsmi2t64:amd64 (0.4.8+dfsg2-16.1build1) ...
Selecting previously unselected package libspandsp2t64:amd64.
Preparing to unpack .../12-libspandsp2t64_0.0.6+dfsg-2.1build1_amd64.deb ...
Unpacking libspandsp2t64:amd64 (0.0.6+dfsg-2.1build1) ...
Selecting previously unselected package libspeexdsp1:amd64.
Preparing to unpack .../13-libspeexdsp1_1.2.1-1ubuntu3_amd64.deb ...
Unpacking libspeexdsp1:amd64 (1.2.1-1ubuntu3) ...
Selecting previously unselected package libssh-gcrypt-4:amd64.
Preparing to unpack .../14-libssh-gcrypt-4_0.10.6-2ubuntu0.5_amd64.deb ...
Unpacking libssh-gcrypt-4:amd64 (0.10.6-2ubuntu0.5) ...
Selecting previously unselected package libwireshark-data.
Preparing to unpack .../15-libwireshark-data_4.2.2-1.1build3_all.deb ...
Unpacking libwireshark-data (4.2.2-1.1build3) ...
Selecting previously unselected package libsbc1:amd64.
Preparing to unpack .../16-libsbc1_2.0-1build1_amd64.deb ...
Unpacking libsbc1:amd64 (2.0-1build1) ...
Selecting previously unselected package libsnappy1v5:amd64.
Preparing to unpack .../17-libsnappy1v5_1.1.10-1build1_amd64.deb ...
Unpacking libsnappy1v5:amd64 (1.1.10-1build1) ...
Selecting previously unselected package libwsutil15t64:amd64.
Preparing to unpack .../18-libwsutil15t64_4.2.2-1.1build3_amd64.deb ...
Unpacking libwsutil15t64:amd64 (4.2.2-1.1build3) ...
Selecting previously unselected package libwiretap14t64:amd64.
Preparing to unpack .../19-libwiretap14t64_4.2.2-1.1build3_amd64.deb ...
Unpacking libwiretap14t64:amd64 (4.2.2-1.1build3) ...
Selecting previously unselected package libwireshark17t64:amd64.
Preparing to unpack .../20-libwireshark17t64_4.2.2-1.1build3_amd64.deb ...
Unpacking libwireshark17t64:amd64 (4.2.2-1.1build3) ...
Selecting previously unselected package wireshark-common.
Preparing to unpack .../21-wireshark-common_4.2.2-1.1build3_amd64.deb ...
Unpacking wireshark-common (4.2.2-1.1build3) ...
Selecting previously unselected package tshark.
Preparing to unpack .../22-tshark_4.2.2-1.1build3_amd64.deb ...
Unpacking tshark (4.2.2-1.1build3) ...
Setting up libssh-gcrypt-4:amd64 (0.10.6-2ubuntu0.5) ...
Setting up libnghttp3-3:amd64 (0.8.0-2) ...
Setting up libsbc1:amd64 (2.0-1build1) ...
Setting up libsmi2t64:amd64 (0.4.8+dfsg2-16.1build1) ...
Setting up libbcg729-0:amd64 (1.1.1-2build1) ...
Setting up libmaxminddb0:amd64 (1.9.1-1build1) ...
Setting up libsnappy1v5:amd64 (1.1.10-1build1) ...
Setting up libopus0:amd64 (1.4-1build1) ...
Setting up libcares2:amd64 (1.27.0-1.0ubuntu1.1) ...
Setting up libspandsp2t64:amd64 (0.0.6+dfsg-2.1build1) ...
Setting up libsctp1:amd64 (1.0.19+dfsg-2build1) ...
Setting up libwireshark-data (4.2.2-1.1build3) ...
Setting up liblua5.2-0:amd64 (5.2.4-3build2) ...
Setting up libnl-genl-3-200:amd64 (3.7.0-0.3build1.1) ...
Setting up libspeexdsp1:amd64 (1.2.1-1ubuntu3) ...
Setting up libopencore-amrnb0:amd64 (0.1.6-1build1) ...
Setting up libwsutil15t64:amd64 (4.2.2-1.1build3) ...
Setting up libiperf0:amd64 (3.16-1build2) ...
Setting up libwiretap14t64:amd64 (4.2.2-1.1build3) ...
Setting up iperf3 (3.16-1build2) ...
Setting up libwireshark17t64:amd64 (4.2.2-1.1build3) ...
Setting up wireshark-common (4.2.2-1.1build3) ...
Setting up tshark (4.2.2-1.1build3) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for libc-bin (2.39-0ubuntu8.9) ...
Processing triggers for man-db (2.12.0-4build2) ...
Processing triggers for shared-mime-info (2.4-4) ...
krina_paghadar@Krina:~$ sudo sysctl -w net.mptcp.enabled=1
sysctl: cannot stat /proc/sys/net/mptcp/enabled: No such file or directory
krina_paghadar@Krina:~$


## User:
11/05/2026 18:20

krina_paghadar@Krina:~$ sudo sysctl -w net.mptcp.enabled=1
sysctl: cannot stat /proc/sys/net/mptcp/enabled: No such file or directory
krina_paghadar@Krina:~$ multipass launch 24.04 --name mp --cpus 2 --memory 4G --disk 15G
Command 'multipass' not found, but can be installed with:
sudo snap install multipass
krina_paghadar@Krina:~$ sudo snap install multipass
2026-11-05T15:45:09+03:00 INFO Waiting for automatic snapd restart...
2026-11-05T15:45:10+03:00 INFO Waiting for automatic snapd restart...
2026-11-05T15:45:11+03:00 INFO Waiting for automatic snapd restart...
Download snap "gtk-common-themes" (1535) from channel "stable"                                        38%  274kB/s 3m37s

its taking time


## User:
11/05/2026 18:21

PS C:\WINDOWS\system32> winget install Canonical.Multipass
Found Multipass [Canonical.Multipass] Version 1.16.4
This application is licensed to you by its owner.
Microsoft is not responsible for, nor does it grant any licenses to, third-party packages.
Downloading https://github.com/canonical/multipass/releases/download/v1.16.4/multipass-1.16.4+win-win64.msi
  ██████████████████████████████  62.2 MB / 62.2 MB
Successfully verified installer hash
Starting package install...
Successfully installed
PS C:\WINDOWS\system32>


## User:
11/05/2026 18:22

PS C:\WINDOWS\system32> multipass launch 24.04 --name mp --cpus 2 --memory 4G --disk 15G
multipass : The term 'multipass' is not recognized as the name of a cmdlet, function, script file, or operable
program. Check the spelling of the name, or if a path was included, verify that the path is correct and try again.
At line:1 char:1
+ multipass launch 24.04 --name mp --cpus 2 --memory 4G --disk 15G
+ ~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (multipass:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException


## User:
11/05/2026 19:37

PS C:\WINDOWS\system32> multipass launch 24.04 --name mp --cpus 2 --memory 4G --disk 15G
[2026-11-05T18:29:37.649] [error] [mp] Could not unregister VM: Process failed to start: The system cannot find the file specified.
launch failed: Could not generate a new UUID: Process failed to start: The system cannot find the file specified.
PS C:\WINDOWS\system32>


## User:
11/05/2026 19:59

see listen my teammate said that lets leave the code we will just say him that we have done the theory part only so better ask from there
so as of now lets make the github minimal simple and direct and sturctured about whatevr we actualy have done so that he does not question, use references and all that we used for out study and understadning, cause he definitely goes and checks what all is done in the github while we present


## User:
11/05/2026 20:04

i had given u all the details already about the project name and ID and all ig, AI usage we will add in the github later before deadline
i cant see the repo in my github: https://github.com/Krina-Paghadar
please do it for me , if u need sign in then show me here i will do it and project id is not project 2 okay that is just the name of the project thats it 
id is same as last time


## User:
11/05/2026 20:09

yeah i have done and made the repo and yeah team id is T007
https://github.com/Krina-Paghadar/CS331-T007-MPTCP-vs-MPQUIC


## User:
11/05/2026 20:11

okay listen from here , i just amde the repo as of now
give me the prompt for antigravity to do all the work i wanna do including everything


## User:
11/06/2026 01:36


## User:
11/06/2026 01:37

> File: Final Project Report Template 1.docx

> File: CS331_T007_Report.pdf

here you go with both the tempate once more and also the report


## User:
11/06/2026 01:41

give me the final updated report please then


## User:
11/06/2026 02:15

The current six-page report is good. Please make ONLY the following final updates. Do not rewrite the report, change its structure, or increase its length unnecessarily.

1. Appendix A – Krina's contribution: Replace the existing description with:

"Studied MPTCP architecture and connection establishment, including MP_CAPABLE and MP_JOIN; the distinction between TCP sequence numbers and Data Sequence Numbers (DSNs), DSS mappings, ACK mechanisms, retransmission and reinjection, and path management using ADD_ADDR, REMOVE_ADDR and MP_PRIO. Also discussed the conceptual roles of scheduling and coupled congestion control, and compared MPTCP with MP-QUIC."

2. Appendix A – Swamini's contribution: Inspect the ZIP file I have provided and update her contribution based on her actual work. It covers multipath fundamentals, research analysis, applications, congestion control, scheduling, QoE, protocol history, end-to-end protocol traces, diagrams and literature comparison.
Specifically acknowledge her study of these two papers:
   * De Coninck and Bonaventure, Multipath QUIC: Design and Evaluation (CoNEXT 2017).
   * De Coninck and Bonaventure, MultipathTester: Comparing MPTCP and MPQUIC in Mobile Environments (2019).
Do not claim she conducted experiments.
3. Appendix A – Kaushal and Pratik: Retain concise descriptions based on their assigned topics in the condensed plan. Their progress is approximately 60–70%. Do not claim they read RFCs or executed tools unless confirmed. Pratik's work is conceptual, not actual experimentation.
4. References: Keep the bibliography minimal. Retain:
   * RFC 8684 (confirmed read by Krina).
   * The CoNEXT 2017 paper.
   * The MultipathTester 2019 paper.
Add these paper links to the corresponding bibliography entries:
   * https://inl.info.ucl.ac.be/system/files/conext17-deconinck.pdf
   * https://inl.info.ucl.ac.be/system/files/multipathtester.pdf
Add in-text citations where their published findings are discussed. Remove other references that are not genuinely used or confirmed by the team. Do not invent bibliographic details.
5. Technical corrections:
   * Introduction: Clarify that ordinary QUIC supports connection migration but does not provide simultaneous multipath transport by default.
   * Page 2: Verify the MPTCP token and initial DSN derivation against RFC 8684 Section 3.1.
   * Page 2: Correct the explanation of MPTCP fallback against RFC 8684 Section 3.6.
   * Page 2: Verify MP-QUIC path and Connection ID terminology against draft-ietf-quic-multipath-21.
   * Page 3: Refine the head-of-line blocking explanation so it does not imply complete isolation between all QUIC streams.
   * Remove or qualify any unsupported claims about adoption, implementation availability or deployment.
6. Appendix B – AI usage: Keep the existing concise AI disclosure table. Do not put raw conversations inside the PDF. Mention that actual prompts and conversation logs will be maintained separately in the GitHub `AI_Used/` folder. Include links or filenames only once those files exist. Do not invent model versions or logs.
7. Keep the current report structure, formatting and approximately six-page length. Leave member ratings blank for the team to decide. Do not add new sections, graphs, results or implementation claims.

Return the updated PDF and editable DOCX, along with a short list of changes made and anything still requiring team confirmation.


## User:
11/06/2026 02:26

> File: MP-QUIC_vs_MPTCP_Final_Project_Report.docx

this is what rathi made
he told to add my (Krina) part in this and add swamini and pratiks part as i told you and idk about rating we are not sure yet it is said to be unique and whatever everyone agrees upen, so rn we have thought of 10 9.5 8.5 7.5 or idk what they mean by unique and pratik said he said RFC 6356 and he didnt read mininet paper is left to read
now update this with what i said and give me final other things check and keep it and format and all keep the same it is already good enough
bro i told u keep the same format as the docx i have attached just update the changes mentioned above dont change the format


## User:
11/06/2026 02:31

The current report is becoming too detailed again, especially the Evaluation section on pages 5–7.
Please make the following changes only:

1. Evaluation: Substantially shorten this section. We do not need extensive numerical benchmark tables, five different performance scenarios, or long application-specific recommendations.
2. Keep a small qualitative comparison table and a concise discussion of the findings from the two studies actually covered in Swamini's literature work:
   * De Coninck and Bonaventure, CoNEXT 2017.
   * MultipathTester, 2019.
3. Remove detailed numerical claims such as 35–50% improvements, 15–30% latency reductions, 95% goodput recovery and 60% retransmission reductions unless they are directly verified from the original papers and are genuinely necessary. Do not present published findings as our own results.
4. Reduce the lengthy congestion-control and scheduler discussion. Retain only the essential conceptual explanation needed for our MPTCP vs MP-QUIC comparison.
5. Shorten the Summary. Avoid repeating all the findings and technical details from earlier sections.
6. Remove the detailed MPTCP configuration commands from Reproducibility. We did not execute them. State simply that no experimental setup or scripts were developed, and distinguish the reviewed literature from our own work.
7. Keep Swamini's contribution based on her actual ZIP, but do not attribute every numerical finding in the report to her.
8. Leave member ratings blank until the team decides them. Correct Appendix B to reflect the AI tools actually used, and do not claim raw logs are uploaded until they are.

Preserve the official template, current formatting and concise academic style. Do not add any new content or sections.
Our priority is a short, understandable report that accurately reflects what we studied and can defend during evaluation.


## User:
11/06/2026 02:50

> File: MP-QUIC_vs_MPTCP_Final_Project_Report_v3.docx



---
Powered by [Claude Chat Export](https://claudechatexport.com)

---

# Antigravity

_Raw prompts given to Antigravity._

## Antigravity Prompt 1

# Prompt for Antigravity: CS331 Project (MPTCP vs MP-QUIC)

Copy everything below the line into Antigravity. Before you send it, put these files in the workspace folder: `Final_Project_Report_Template_1.docx`, `mptcp-mpquic-understanding-plan.md`, `mptcp-mpquic-plan-condensed.md`, and your repo clone.

---

## Role and goal

You are helping a team of four students finish a university Computer Networks course project (CS 331) due **Friday 6 Nov 2026, 10:00 AM**. Produce the GitHub repository contents, the technical report, and the presentation. Everything must be **truthful and defensible**: the professor will question the team on every line.

## Project

- **Title:** MPTCP vs MP-QUIC: A Comparative Study of Multipath Transport Protocols
- **Team ID:** T007
- **Project ID:** ask me; do not guess
- **GitHub repo:** `CS331-T007-MPTCP-vs-MPQUIC` (owner: Krina-Paghadar), already created and empty
- **Team:**
  - Kaushal Rathi, 24110290: QUIC and MP-QUIC design; leads the comparison
  - Krina Paghadar, 24110169: MPTCP design, history and adoption
  - Pratik Kumar Dhakar, 24110277: congestion control, fairness, scheduling; methodology; end-to-end analysis
  - Swamini More, 24110211: published research findings and application implications

## What the project actually is (non-negotiable)

This is a **theory and literature study only**. The team has:
- Read RFC 8684 (MPTCP v1), RFC 6356 (coupled congestion control), RFC 9000, RFC 9002, and the draft draft-ietf-quic-multipath-21.
- Read the CoNEXT 2017 "Multipath QUIC: Design and Evaluation" paper and the MultipathTester paper.
- Prepared a design comparison and an adoption analysis.

The team has **NOT**:
- Written any protocol code.
- Configured or run MPTCP or MP-QUIC.
- Run any experiment or produced any measurement of their own.

(They tried to set up a Linux test machine. WSL2 on Windows has no MPTCP in its kernel, and a Multipass VM failed to launch. They did not pursue it further.)

## Hard rules

1. **Never invent** experiments, results, numbers, graphs, code, screenshots, implementation status, or citations. Every number must come from a cited source and be labelled as such.
2. **Do not imply** the team ran anything. Never write "we measured", "we tested", "our results show", or "we implemented".
3. **Label every claim** as one of: *specification* (RFC or draft, with the section), *published research* (the paper, under its own setup), *existing implementation* (how a named build behaves), or *our analysis*.
4. **Citations:** use only sources listed here or that you can open and verify. If you cannot verify a detail (author list, page numbers, a figure), write it as "[verify]" in the text and tell me. Do not guess.
5. **MP-QUIC is not an RFC.** It is an IETF draft (draft-ietf-quic-multipath-21). Name the draft whenever you describe it.
6. **Do not inflate** the project. If something was not done, say so plainly. Do not add filler files or empty folders.
7. If you lack information (Project ID, member ratings, AI log filenames), **ask me or leave a clearly marked placeholder**. Never fabricate it.

## Facts to keep straight

- Linux MPTCP has been upstream since kernel 5.6 and speaks MPTCP v1 (RFC 8684) only. Older papers mostly used the out-of-tree v0.96 fork, so their numbers are not directly comparable to the upstream kernel.
- The 2017 "MPQUIC" was a research fork of quic-go on pre-IETF QUIC.
- Draft-21 terms: `initial_max_path_id`, `PATH_ACK`, `PATH_ABANDON`, one packet number space per path.
- MPTCP uses two sequence spaces (per-subflow and data-level) with DSS mappings and Data ACKs, so that each subflow looks like normal TCP to middleboxes. Fallback to plain TCP happens when options are stripped.
- MPTCP is limited by middleboxes, kernel dependence and application indifference. QUIC multipath is still being standardised.

## Task 1: Repository

Create this structure and keep it minimal:

```text
README.md
code/README.md          states plainly: no code, why (WSL2 kernel has no MPTCP; Multipass failed), what we did instead
report/                 final report PDF goes here
ppt/                    presentation PDF/PPTX goes here
AI_Used/README.md       index table only; the team adds the raw logs themselves
```

The README must contain: Team ID, Project ID, title, all members with roll numbers and roles, overview and scope, a "what we did / did not do" table, the sources list, and the repository layout. Do not touch `AI_Used/` beyond the index table.

## Task 2: Report

Use `Final_Project_Report_Template_1.docx` **exactly as given**: keep all headings, order, numbering (including the template's own quirks), fonts (Times New Roman or Arial, size 10) and the 10-page limit (references and appendices excluded). Fill it in; do not redesign it.

Adapt content to the project like this, keeping every heading:

| Template section | Content |
|---|---|
| I. Introduction | Why multipath matters; why it is still rarely used; what this study covers |
| II. Problem Statement | Compare MPTCP and MP-QUIC on design, deployability and reported behaviour. State scope: a theory and literature study, with no experiments |
| III. Project Objectives | Specific, checkable objectives about understanding and comparing (not measuring) |
| V. Architecture and Design | MPTCP v1 design and MP-QUIC draft-21 design, with a comparison table, design trade-offs and alternatives. Cite the section for every claim |
| VI. Implementation | Reframe as "existing implementations and deployment status": Linux upstream vs the old fork, Apple's use, QUIC implementations. State that the team wrote no code |
| VII. Testbed Setup | Reframe as "methodology of the published studies we reviewed": their setups and limits. State that the team ran no testbed. Mention the failed WSL2 and Multipass attempts in one or two sentences |
| VIII. Evaluation | Reframe as "published results and what they show": summarise reported findings with their setups, and say where they conflict or do not transfer. **No graphs of invented data.** A summary table of cited findings is fine |
| IX. Summary | Findings, why adoption is slow, limitations (including no experiments), future work |
| IX. Reproducibility | Link to the repo, and state that there is nothing to reproduce experimentally; explain how the reader can verify our claims from the sources |
| References | IEEE style as in the template |
| Appendix A | Team work distribution table. **Leave the ratings blank**, with a note that they are agreed by the team and must be unique |
| Appendix B | AI usage table, based on what I tell you; prompts link to the `AI_Used/` folder |

Write it in clear, plain English that a student can explain aloud. Output the finished report as .docx and also as PDF. Check the page count and report it.

## Task 3: Presentation

About **12 slides**, concise and technical, following the order the team studied in:

1. Title and team
2. Why multipath: Wi-Fi plus cellular, yet rare in practice
3. MPTCP design: TCP options, subflows, two sequence spaces
4. MPTCP handshake and joining (MP_CAPABLE, MP_JOIN, token and keys)
5. Coupled congestion control and fairness
6. QUIC and MP-QUIC design (draft-21)
7. Side-by-side comparison table
8. Implementations today
9. Why MPTCP is not widely adopted
10. Published results, with their setups
11. Limitations, and what we did not do
12. Recommendations by application (video, file transfer, VoIP), and conclusion

Add short speaker notes saying which source supports each slide. Use diagrams you can draw accurately from the specs. Use no invented numbers and no screenshots of things the team did not run. Export as PPTX and PDF.

## Task 4: Self-check

Before you finish:
1. List every factual claim that you could not tie to a source, and every "[verify]" item.
2. List every place where wording could be read as implying we ran something. Remove them.
3. Confirm the report is within 10 pages.
4. Give me a list of the 10 hardest questions Sir could ask about this report, with short honest answers.

## Output

Produce the files, then give me a short summary: what you made, what is still blank, and what I must verify myself. Ask me for anything missing before you guess.

repo: https://github.com/Krina-Paghadar/CS331-T007-MPTCP-vs-MPQUIC

## Antigravity Prompt 2

bro u had to update in my actual repo:
https://github.com/Krina-Paghadar/CS331-T007-MPTCP-vs-MPQUIC
i had made the repo already with the name, ik its private but u had to update everything here, and it has no relation to dvfs assignment at all, that is different forget it, update in this above repo man, if u need sign in then show me here i will sign in for u and u may work
