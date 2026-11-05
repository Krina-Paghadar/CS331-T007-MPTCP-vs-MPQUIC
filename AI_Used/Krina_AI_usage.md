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

**Created:** 10/17/2026 14:34:44  
**Updated:** 11/6/2026 3:01:47  
**Exported:** 11/6/2026 3:25:22  
**Link:** [https://chatgpt.com/g/g-p-6adb348b46c88191920f931e2f9b31b8-cn-project/c/6ad33a2b-975c-83ee-81d5-419e8341aa0f](https://chatgpt.com/g/g-p-6adb348b46c88191920f931e2f9b31b8-cn-project/c/6ad33a2b-975c-83ee-81d5-419e8341aa0f)  

## Prompt:
17/10/2026, 14:40:15

CN sameer sir meeting - Transcript

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

[Screenshot omitted from log: 1793881777979_image.png]

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


## User:
11/06/2026 03:35

I need you to create a single Markdown file named `Krina_AI_usage.md` for submission in the `AI_Used` folder of my project GitHub repository.
Repository: https://github.com/Krina-Paghadar/CS331-T007-MPTCP-vs-MPQUIC
Instructions

1. I have attached two Markdown files containing my complete conversations with Claude and ChatGPT. Include their contents exactly as provided, without summarising, paraphrasing, rewriting, or cleaning up any conversation.
2. Apart from these two files, I also used Antigravity. I am providing the following two prompts that I gave to Antigravity. Add them to the same Markdown file as raw prompts:

Antigravity Prompt 1:
`antigravity prompts: pasted (third)`
Antigravity Prompt 2:
bro u had to update in my actual repo:
https://github.com/Krina-Paghadar/CS331-T007-MPTCP-vs-MPQUIC
i had made the repo already with the name, ik its private but u had to update everything here, and it has no relation to dvfs assignment at all, that is different forget it, update in this above repo man, if u need sign in then show me here i will sign in for u and u may work

3. Organise everything into one Markdown file with clear headings indicating which content belongs to ChatGPT, Claude, and Antigravity.
4. Preserve the original conversation content, including prompts, responses, follow-up instructions, and technical discussions. Do not omit any content from the two attached Markdown files.
5. Do not introduce summaries, interpretations, or additional explanations. The objective is to document the actual AI usage history in its original form.

Important

* The DVFS assignment is a completely separate project and has NO relation to this MPTCP vs MPQUIC project. Do not include any DVFS-related material unless it appears in the attached raw conversations and is genuinely part of the supplied files.
* Do not modify my existing GitHub repository or upload anything. I will upload the final file myself.
* Ensure the Markdown formatting preserves readability while keeping the actual conversation text unchanged.

Final Deliverable
Generate the complete downloadable Markdown file named exactly:
`Krina_AI_usage.md`
It must contain the entirety of both attached conversation files and the two Antigravity prompts.
And keep it formatted, means chatgpt prompts under chatgpt and so on


# User:
11/06/2026 03:41

wtf is this:
in the md file???
it is showing as a link in the repo when i uploaded the md, either dont add the image its fine, prompt is necessary, cause this would look weird, change everywhere if there is such a long link


# User:
11/06/2026 03:59

this part :

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
is coming bold on using urmarkdown in the repo on preview

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
