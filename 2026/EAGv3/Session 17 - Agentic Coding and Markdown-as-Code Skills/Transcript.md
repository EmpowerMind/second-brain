## **EAGV3 Session \- 2026/08/15 10:47 IST \- Transcript**

# **Transcript**

### 00:10:00

Sairaj Nadaf: Morning This

### 00:15:00

The Admin: Good morning everyone. You can hear me. Just say hello.

Sairaj Nadaf: Okay.

Vikas Gupta: Hello.

Rajesh Joshi: Hello.

The Admin: Happy dependence On the eve of only because today is Independence Day, we're going to be releasing a new agentic capability and that's coding and especially marked down as a code skill. But before I do all that, let me start ing. So as I said, this session is on coding. we've done everything that agents can do but not the coding part and there were reasons for it. We had left lot of hooks that is going to make our coding agent much better.

The Admin: I think that you're already aware of the sandboxing of the systems and especially the GLC where we can have a really good supportive model that can continue to build. Now at the end of this today this is what you can build. This is built by the same harness that is already there for S7 working JavaScript tested and some of the other stuff. there's a hack also that is involved and that's a part of the hardness. So that's why you need to know what the hack is to make sure that your free tools can do this. So I hope that by the end of the session you can understand what is required to make a coding hardness and what we have is already good for it.

The Admin: what would needed to move it towards the coding part and enjoy basically and there are a lot of things that may think and does not involve coding but they do for example even a file edit let's say you want to just ask a simple thing there's a PDF can you please remove the last page and share it again can you compress the PDF can you edit a document can you save it as markdown or let's say doc or pdf all of these are involved tools and coding reliability so that is why this session is really gives you and your agent extra depth to what they can actually do. here had This is inline CSV that is written by the agent. Zero external files and some around 35 or 53 KB. So good job done. I took efforts

The Admin: to make sure that can make something like this. But the prompt and everything is in the code and you can try it out. Here's the prompt actually. Create an index.html A complete production quality landing page for fictional developer tool called actress that runs automous coding agents. One self-contained file, no build steps, no external files of course need to explore a lot. And' This was written by a prompt agent itself which takes the prompt that we give understands the harness a bit and improves the prompt. So it knows what is it that the agent can do. So that is also enabled. there's a toggle for that one or zero depending on what it can whether you want to do it or not. But you can enable this right and using that it can come back and build things for you. when you go to lovable and make some pages there or when you think you are just asking Gemini or Opus to make a page for you do not assume that it's not doing it. This is the task of Harness is injecting these kind of things. Looks at the code assumes this is how the modern thing should look like.

The Admin: expands it builds some thoughts and then put it inside right so this is not a hack this is required hack is something else that I'm going to explain do we have a toggle I don't know to not this okay was there check I removed something and forgot to add that. imagine that we do have a toggle button on the page. There was something else that I removed and then I added this. U when you ask your model to create HTML page, it does everything and it thinks it has added a toggle button also and when you click on it the CSS never captured it right build some feature that is not end to end linked and then you basically get a page where things are not working. The agent think it's done but it's not working.

The Admin: So the question is that who's going to tell the agent now right now So you're going to go back and say my toggle button is not working and then can you please fix that break something else. So we need to have some system where this can be controlled and that again is the part of the harness and that's why this session essentially otherwise coding agent is literally add three-fold tools and it should be good to go. Now we have never written any code. Our agents were not allowed to write any code. But from today that changes. It can write Python code. It can write HTML code and if you want to add more languages this capability was locked to us only we can write code. When know you say we basically plot code or your codeex the code is the first work this agent does. what is different about anything else? Let's say you ask your agent to go online figure out some schedule for Tokyo it and give it to you.

### 00:20:00

The Admin: There's no way you can check it properly right unless you manually go and figure out if you ask that give me the 10 best flights this month to Canada it can come back and give you result but you can't really test coding is the first thing or code is the first thing that is testable that can have a test file that can be expected to give a specific result or it is a part of it right you can test it out the question now is that who's going to test it either the test is already there which is what we will assume that if you're getting a particular code if you're not following a test-driven development with your agents then you're already doomed so do not come after two weeks of effort with agent and say that okay agent doesn't work agents

The Admin: Agent decoding is always supposed to be a test-driven development process. So when you're writing a code with your agents and you're not asking to create a test file gone you please do not assume that will work. That's why you keep seeing our test keeps on bloating. Right now we ask someone for a test when we are writing a code. So assuming the test is there either you're writing it or you're asking other agent to write the test and then you're asking the feature to be there becomes testable. Sometimes the results are expected sometimes the speed can be checked. Sometimes for example if I run a simple image compression code or my agent does and the image is compressing for last 1 hour I think I know something is wrong and we can cut so we have some sort of time boundary as well.

The Admin: But the problem also is that in the session 15 we needed a judge to answer right and the judge is going to be another model in session session 16 we had a human to essentially approve something that is very critical code has a judge already if there test is determined deterministic instance it's free and written by somebody else now that somebody else need to be either another folk of a harness or another agent that is not allowed to be changed or disturbed otherwise it will cause big issue, So, please remember that when you're talking about your agents writing test in your flow for enterprise, follow the test-driven development. there's something to be done by your agent. You're about to ask some agent to Launch an agent first that writes those tests and keeps things ready and after that launch another agent that actually writes the code for that. Writing a test is easier, boring. That's why we don't do it.

The Admin: So everything is in S7 code and running on 8113 and GLCV5 is 81\. Now here are things that we had to do. First of all the guard. py is protecting paths of things coding agent cannot update or cannot change. This is where your test might be there. This is where some of the files you do not want access to be there. This is the thing where your agent is not supposed to go. Then we have edit. py this is a very very specific rule that nearly every single coding harness follows and we have stolen from them and it will feel very logical once you understand what it is the rule says you cannot edit a file unless you have read it very simple rule so edit py basically tracks whether an agent has read a particular file or not right so it's an anchor edit you can only edit something if you have read it that means that if a blank call is sent that

The Admin: swap this particular Gemini key with some other key it might get caught. So there are limitations to that's a bad thing right let's say we have Gemini 2.0 zero it got obsolate. Now we need to move to Jet 2.5. and you're letting the agent write a code and it is going to change all. These are sometimes where cloud code comes back and asks you hey are you sure you want to do it because now it's passing the responsibility to you that you only did it. I was just saying but you went ahead and clicked okay change everything that we are supposed to read terms and conditions. Then we have executed py. We already had something like this in u u v2. In fact this was a big deal there.

The Admin: So that code is something that is very simple and leveraged. Exit py is essentially the command runner with no shell or allow list. So you send the command, it runs it and then you get the result. Right? That's where the execution lives. Then we This is the validator on its own agent. the validation is there for HTML CSS very simple for Python. You have to come up with few other things on what all you want the code to be tested against. Then we have skills. You put a skills.mmd inside it. It becomes a new skill or a new feature that your agent can work on.

### 00:25:00

The Admin: We'll go in more detail about what skills is for the code coder because not only for example your own code base right now in your own codebase let me talk about myself the action and then we have a caddy file system then we have cicd on github then there are myql storage bases there are live production then there are a lot of things that are happening right now if I am out of context and now suddenly a new agent has to be launched.

The Admin: I can't tell it to read all the code and then update my chat that I did for example yesterday right I need to maintain a skilled MD and I'm only going to ask my agent hey can you please read that skill.md it knows what not to touch right so everything goes through CD then there's a tracking and other so that also happens so similarly if you have a very simple feature also edit a PDF when you do that you can ask it to make sure that you're making sure images are 72 dpi Okay, the file size is not three more than 3 MB. it is not writing any passwords or stuff. File names are always something like XYZ. So you've added some hidden watermarks. So all of that becomes your skill.md. So it's not just telling the agent this is where the O keys are. It is to have additional behavior. So every time that behavior is locked in whenever agent works. And finally we have reasoning which is a draft verify refine.

The Admin: Essentially it means that before it writes something it need to get a draft of that then verify that this is going to work and then refine So there's a sequence of things that are going to be working In the code the words will change so we'll see what those things Two existing files are changed. Land. PY has learned Some works Code will need repeating. So it allows the coder to repeat itself. Right now till now what was Planner will launch a plan. It's going to say that hey resizer go online and figure out stuff for me and gets the results and proceed. Now the coder will come back to the planner I think I made a mistake in last step. I need to do it again. And planner is okay with that. Plan is not going to change the plan. It's not going to keep on updating or adding nodes. Right?

The Admin: So the coder will run itself call self basically it's going to keep on repeating itself it's till the job is done you can decide how many times or how many depth the coder can actually run now calling itself is not a feature in network x so it will end up looking like a node but essentially it's calling itself and the runtime py it gain nine coding capabilities and a nested run scene so there are nine things that we had to add these

The Admin: are sort of tools we going to see which make our life very easy to edit cloud codeex Hermes if you've used Gemini all of them they have literally 9 to 12 tools that's all they have and they use that magically very well to do everything you have seen them doing okay and okay so how cloud code cursor wins of Gemini or Hermus or any other thing that you have seen actually work.

The Admin: Before building we need to know that is there something special about them all of them follow nearly the same hardness right you'll not feel the hardness is actually becoming bottleneck because each of them keep studying themsel and we are sort of at a place where most of the behavior is sort of locked what the hardness is supposed to do first of all it read files all the hardness when you open a repo or a new code base it's going to read the file that's the first thing that's building the context itself it will not read all the files

The Admin: That is also important. If you have 200page PDF just as a reference for your chip development, it's not going to read all and exhaust the context. It's going to find few that matters and read the part of those. So it's being smart about what do I need to read. Sometimes it's just going to read the initial few lines and understand So it may open all but figure out not required very fast and just keep dropping them. And for that it can launch small agents to understand that this file is not important for me just throw it away. That's the initial phase. Then it edits by naming a place not by generating a file. It's very very important. let's say we ask our coder to change the name of application or that HTML the company name there actress instead of actress let's say it mentions let's say big bear. it's not supposed to create a file and then inside the file edit it. No, it is not supposed

The Admin: to tell the line number in the code and edit it. Now it is not supposed to even give a diff. Earlier it is this. Change It is going to edit by naming a place. It needs to tell the lines and the content inside the line that I want to read for example return something and go there and then change it. We going to see why this is important. So no line numbers, Even case of HTML when we creating new file HTML file needs to be there and then it needs to go inside and then find something to place something there right so even if HTML empty is there it needs to say that I've at the empty line paste this a very simple rule and preserves and protects in a lot of ways now it run commands mostly tests and this is the one that is going to tell if anything was right or not right so the commands are there mostly to test whether things are working or not right it's not

### 00:30:00

The Admin: to delete other stuff and you're going to see that cloud code and all other actually do something like that. It looks until something says it can be a passing suit. We have written pass a test and we says okay we are good a limit you can only run 10 times or a person says done I don't want you to run further right that these four lines are really the architecture of all the agents that are there claw code codex fins suffer any questions on this course yes of course we have our sandbox

lakshmanarao vanimisetti: Do we need a sandbox to run the commands? Okay.

The Admin: inside exec and when you use clot code you do auto because now you are sure that okay it is anyway my code has the sandbox is it controls something what you're referring to is basically this clot code is going to live in a terminal so the control runs the center each ask permission at a different boundary moment they are very close to the sandbox kind of thing it's going to ask you and that boundary is the product developer's decision so it is your decision

The Admin: ision who's going to decide what is that sandbox not the technical hard fact so all of them have a very different kind of sandboxes and clot code when you say auto has access to everything still it has internal things that r minus rf kind of stuff is hard block even if you have put it in auto mode because yes so the four lines are now the four next topics Hello.

Vikas: Hi everyone. So can you elaborate a bit more on the editing importance of naming the place not by region? Okay, sure. That's

Raghu Rammohan: So you're saying it file not all of them right but sometimes if we give that keyword at codebase or something it will read all of it right it's like in Okay.

The Admin: Yeah, not all of it. It will read. Okay. How do I say? It will open all of it. It will try and read as little as possible to understand whether I need to read this file or not.

Raghu Rammohan: So if we don't even give that code base…

The Admin: Okay.

Raghu Rammohan: then it picks whatever it feels right. Okay.

The Admin: So, the permitted,…

lakshmanarao vanimisetti: from the MD file. yeah this MD file does it requires have a detail level as tree level that level of a abstract syntax tree

The Admin: can you please raise your hand so I know who I'm talking? No, no, it's not working. Yes. No. some people tried to make it. It was a nightmare to manage it. And that's why this is what people jumped back to. This was way more easier compared to because the same law work for all the code. Python has it own then C will have its own. Dash.

Avinash Anad: Hello Ron I tried some creating similar thing previously and…

The Admin: Answer is money.

Avinash Anad: after running a while the local llm context was stopping the file from reading completely. So okay so that I fixed in I like your default ladder you have right so I fixed in that ladder and divided the file to different chunks and then passed that as a file and then started making sense

The Admin: Yes, I'm hearing a lot of good news about this. I have not tested it yet. Quinn 2 3.8 actually I think.

Avinash Anad: Okay, next.

The Admin: Yeah, this is there now.

The Admin: It's there on ama also and looks stunning.

Avinash Anad: Okay. Yeah.

The Admin: It is unit because I have that kind of RAM but 4.6 six max kind of capability on 27B using 17 billion 17 GB RAM is ask…

### 00:35:00

Avinash Anad: M 4.7 is also good community support.

The Admin: but I keep the feedback on in Reddit people come back with all their pain and

Avinash Anad: Yes I'll try 3.82.

The Admin: Okay. No,…

Avinash Anad: Thank you.

Anubhav Panda: for large code bases right for example learning into GBS do they also use rag kind of approach Yeah.

The Admin: no. rag is to see when you say rag you're literally talking about billions of points and understanding the semantics would be that I love my dog and in some other statement I love my country. So you need to be able to differentiate between that.

The Admin: when we talk about coding the code cannot have some sort of embedding if you think about it right x++ col …

The Admin: then different symbols it's very difficult to figure out a semantics there is no rack kind of model for code so you'll not be able to find right and we are not matching a code with a code we're matching we're trying to find something and edit it basically so in that case you will see claude reading the code it's going to say I'm reading big file 500\. Let me eat next 500\. Nothing. Reads has to be read.

Anubhav Panda: So based on the model weights only it will understand the code and then try to figure Yeah.

Anubhav Panda:&nbsp;

The Admin: So let's say you have coen 3.8 So the context length is there but it's not as good as let's say opus 5\. So you can do divide and rule. You can ask the agent to launch another agent that reads and come back and tell you that okay is this good enough or not?

The Admin: We are increasing the overall number of calls to the agents or the LLMs but we're not destroying the context of the main agent.

Anubhav Panda: Okay. Just

The Admin: Let it cheat. Here's a real function and this is how our code also behaved initially before becoming There's a function. It says define average mean of a list return zero for empty list and this is the overall function. if you remember how to read code or write code, there's an error already. It says it's going to return zero for empty list. But if you send zero inside is going to crash, right? The doc string promises zero. And if we do send zero inside, it's going to write zero division error. So a test says so and it's going to fail essentially. if you say ask an agent that make this function pass the test, it's going to figure out four ways in which it can pass a test.

The Admin: First is delete the failing test. And if you think this is not true, both the open AI and were found doing exactly this to hugging face where hugging face was making remember the hugging face challenge as of now. It was supposed to do something and just went there and deleted a test so it can pass it. Second is at pi test.mmark.s skip. So it's going to skip the test. It's not failing the test again. Assert that if average 00 equal to and assert blah blah is not none. And if you're getting something like that, then it's change the test itself. So you can't even test it. And finally wrap the whole function around try and catch to fix the test. So if the average does give you division by zero, it is going to find it and it's going to say okay it. If then just return zero. So now it's again not failing the test, So the only way to fix it properly is to actually return zero inside somewhere if the numbers is zero.

The Admin: But apart from that there are four other ways to pass the test. And this probably happens a lot more than we actually know because none of us are reading the code. So this is not dishonesty. You really did ask the model to figure about the way in which the test is not passed and sometimes you may actually want it also you may not want to fix it and just don't want the test to crash right so agent can write the code but cannot write things that is going to grade the code so that is something that is still on us or some other agent who's going to review the code and then come back with the proposal so now we need a reviewer also test files test py CI config packaging all can be refused before an edit is attempted right so

The Admin: your agents can get into a loop where things are passing or things are clearing or things are getting deployed without any of this running right and logic is not to dis to discourage that in the prompt if you go in the prompt and say that don't do it I want a test to actually pass how many such things can you come up with so that is not the right strategy and we discussed early in the course also that prompting is not prompt engineer is dead basically prompt engineering is nothing today right it's all about skills and other stuff you may now write a skill It may be a part of the skill but probably it needs to be part of the thing that refuses to accept the code right and actually test the code thoroughly and make sure that inside also it's written in a way where you want it.

### 00:40:00

The Admin: So that's fair. If something is trying to change test calculation, I going to refuse it. It's going to change contest, you're going to refuse it. It's going to change the CI/CD. You're going to refuse it. It's going to change the runtime that may be editable because you may want to change something, So there are few things that are just refused to be edited. So you need to have that control. So these are some of the building blocks that you need to be aware of. So again, same thing shown. we have a delete failing test here. We just deleted it. So our test is going to pass. Then we add pi test. Then if you do that it's again going to pass Shortcut again contract again. The actual fix is something like this. So you should be able to catch all of these to make sure that it is actually solving the problem that you have. That brings back to the same thing that why Humans are required to at least do this part or get a agent that can do this part before the code is run.

The Admin: That might seem like a double issue that earlier you supposed to write a code and then test it but now you're supposed to write a code and let the agent test it. Believe me this is faster much cleaner and then you will actually know what you're testing against.

Raghu Rammohan: Ron, I have one question on the Quen part. Can I ask or…

The Admin: Okay.

Raghu Rammohan: part of the last assignment I was trying to use Quen 3 and it said that Quen gives this thinking blocks in the response and the S16 code is not able to parse it. So I was supposed to use Quen 2.x or something like 2.7. So if we use this quen 3 in S7 code will it be able to handle Okay.

The Admin: No, it sounds like a GLC error. u because only GLC is supposed to be looking at it. Just try it out. Maybe it will like

The Admin: And if it's not then we need to create a patch for it. two rules that make an edit very safe. imagine that we given a 400 line file and ask to fix one particular function. it is going to hand you back. This is how things used to be. This is how I als file and you want it to edit a 400 page file. So you send it to fix that particular function. It reads it and then now it needs to write the 400 lines again. It is going to do it but change. Some will be reconstruct from the memory and we will not know what has changed. And that is the problem that we had in the earlier file. In fact this is why suddenly cursor got into picture. Cursor was the first guy or the first company that actually understood no this is not the right strategy. Let it read the code. It's fine. Let understand the whole flow. Perfect.

The Admin: But it is only going to change only a part of it. Don't make the whole thing be written again. So agent It is going to replace the strings. And there are exactly two rules that to follow. First is read To edit the agent that has not read the file, we are just going to remove it. We are just going to refuse it. So the error right now if you run our harness, it's going to say that cannot edit py before reading it. And we know the file was read because you can check in the last context or we know whether the time of reading or opening was there or not. So read the file first editing from memory rewrite codes you never saw and the anchor must be unique. If the text appear twice the edit is refused. What do we mean by that? do I have a code example here. So I can show here only. Okay, let me show it here. So right now for example rewrite the whole file.

The Admin: let's say we're breaking the rule. So in that case this is the code that was sent right and the line six is the bug return total by end number. This is what it did. So you can see that it changed the mean of the list to return zero to mean of the list. I hope you have seen something like this. It keeps on changing the dock string. If that is happening that means that it is not following the laws we talking about. Second is it wrote this if not numbers return zero return. That's fine. The code the error is fixed. But what happened. Total sum i.

The Admin: kg for in items. It changed that to total weights equal sum iw weight and again it's going to fail. So now it has fixed something but unfix something else harness issue. I've seen a lot of people complaining to len that why have you changed that part. here is a un undefined diff which we'll talk about later on. Basically here we saying that if you see here this is what it is saying. I'm going to write all the 14 lines response here it is going to say that go to line

The Admin: something remove this and add this right now if you try and do this patch does not apply hunk one failed at the line number four context mispatch expected total sum numbers found mean of the list here we mentioned the line number four here right but the line number four was something else so there's a problem there because the way the docs are managed based on what program you're running is very different so it will again going to cause an error

### 00:45:00

The Admin: It has to name an anchor. It has to name exactly what needs to be changed. So edit the codec cal. Fair enough. Old string is Return total length. Find that New string is going to be something like this. If not numbers, zero. if the text appears twice, for example, if you had a function because maybe you have another function here where it again says return total/ lend numbers.

The Admin: It's not a function right it may be calculating something else maybe is calculating without the spaces and the code and your system finds two such lines exactly same you're again going to refute lm has to come back with an anchor that is not repeated it has to return enough amount of code exactly written as there in the file for us to make an edit right that that's one of the best thing which cursor and other guys found and then suddenly the code editing editing was in a different domain right so anchor must be unique If the text appears twice, the edit is again refused. If the second one looks like an API constraint, it is a comprehensive check. We are really checking everything in the file to make sure and checking is free. You're literally doing a dock strings search. And why not a diff? Because needs the correct line numbers and lms are really bad at remembering which line it is. it can't keep on remembering think from point of view, right?

The Admin: It has to close your eyes and remember okay how many times did I saw the new space or new line character one two I think four okay four right we don't want something like that no models are not good at remembering the line numbers No,…

Vikas: Two questions first is that line following the line number is not optimal because when you make the changes the line number keeps on changing. And second being how do you decide on the anchor? it should be unique and is it some length constraint or

The Admin: no, no. The anchor is from where? Let's let us open any file. let's go to GitHub opens up. Okay.

The Admin: What is it? J. I'm going to open any random file if I do find need to be secure. How good is this? Okay. Anchor is let us say we want to change this

The Admin: Then this is the angle.

The Admin: If we have another function where verify window normalization is there, the harness is going to say dude, I have found it twice. I can't edit it. Then it needs to increase the anchor window.

Vikas: So we can say it is some sort of a key and…

Vikas: which is very close to what we want to edit. Thanks.

The Admin: And when it responds back, it is going to give response from this side to this side. Right? So if you name an anchor, It's finding return total this line and it's returning and it's changing that part. So if this was there somebody somewhere else, if this line was also mentioned here, then it has to give from return zero to this line.

The Admin: All It has to give from total to this line. Are we clear?

Vikas: Yeah.

The Admin: Running the test and nothing else. Now the judge is only free if the agent can actually run it. So it gets a command runner and that is the very very dangerous thing. We have seen in session 12 what kind of commands or things can leak in and that is why in this session we are going to be using it. We have never used what we wrote in session 12 but session 12 what we made the code that cannot execute or the sandbox and other stuff is something that we going to be using today. Now for bounds in our code there's no shell. So we are not providing any shell for the Agent is just going to give us the text argument. We are going to be executing it in the sandbox. There's an allow list.

### 00:50:00

The Admin: These are the kind of things that it can run. That is still risky. For example, in git there are things it can do. So we may have to have a specific rules for each one of them. For example, in git we just leave this line. Git looks harmless but there are things we are still not going to allow or specifically let it do. And that's why you'll see that agents do come back to you and say that okay should I commit it to the main or master or should I commit it to GitHub. So allowless of command is not a allow list of behaviors, right? It just says that it can use git but there are still some things inside that are not allowed. So specifically the git it can change something locally but can never change something in master unless you get the command from the user. Right? So allow list again does say that you can use all of this looks like that but inside each one of them we have some constraints. The inside of workspace.

The Admin: We do provide a working directory that you're only supposed to edit code here and nothing else inside and bounded which means that a code that is running for let's say you're going to add it 15 minutes you're going to say okay I'm out I can't handle this code anymore or you have waited enough for the code to finish again part of the harness now part of the function that is being run right so the logic here is that you do not let a agent run unconstrained today we are confident that opus 5 can run for a few cards and give you some results. But when you're writing a code and you're using a free LLM and cheap LLM and something you have not paid for and was gifted to you free, I will not run it unbounded for infinite time, Keep that in mind. And of course, there are some commands that really cannot be used. Python minus v, r minus rf, get push, origin main, all of these are refused. And you will think that do I need to sit and write? Yes, of course.

The Admin: because making a small thing and I mentioned it I think here the primitives take a small time don't do this do that but the refusal is what is going to make the product so if you want to make a coding harness if you want to make a product you need to write the refusals and that is actually the product how safe it is how do you test it how do you contain things that are there and not there and even if you give a proper allow list what inside can still not run that is where the logic needs to

The Admin: We clear on this. All Reading everything or all the files that we have in the codebase is literally throwing things. It's just filling the context with stuff that is not required. There are a lot of tools online and I think I mentioned that somewhere in the session also. So there are tools online that will not throw the whole terminal output also to the LM. It's going to look at it extract some small part and then those tools can be used and the harnesses themselves are improving. So you may use some skill today but within one month you will see that that is also obsolete and the agents themselves are improving it right. So reading everything is not reading. So don't let your harness read all the files and then come back to it. There are three capabilities that are going to allow us to work. One is called glob files.

The Admin: It's going to find the path without content. so the files are there and it'll figure out okay These are the files that I should be interested in. Second is G code which is literally to find the files that matter. So GP code is going to just search for the commands on a function that the code needs to know. It's going to pick the whole thing and dump it. So that is interesting and then read the code takes a larger file than one. So glob files find the files that we are interested in. I'm editing Python files. Should I read+ CPH HTML CSV CSS? Right?

The Admin: So glo files basically makes a list. Second is G code when you find a particular function or stuff it basically takes the whole function and returns that right not just one line. So when you say find return numbers it's not going to return that line. It's going to return that whole Smarter way of doing it. Then you read code when you actually have to understand and go through the code and big code it reads a chunk and next chunk right that's the logic of these three main function that are there. So the failure is not in truncation. it is dilution and that's a big problem. So it starts long before anything is going to overflow. The model is reading the code that has nothing to do with it. So please keep in mind now here we have a repository of 12 files the context window is 128k. if the repository had more files the amount of thing that actually mattered was very few. That is why we need to make sure that what is it that matter for the code and those are the things that are provided to it.

The Admin: And these three functions do a lot of great work. Even if you increase the context and if you still send the files, you're still wasting it, It doesn't make sense at all. You can see that 128k tokens Actual signal was 1% Outcome is lost. It still can't make out anything because whole code has been read. Are we clear on this? In fact, if you're using plot code or anything else, download S7 code and ask it, can you quickly read it and tell me what this all about? and it's going to take few reads and come back to you and you will see that it's not read all everything. Okay.

### 00:55:00

The Admin: A loop is a straight line and that's an interesting thing because loop sounds like that we have something looping in but because we using network X as I mentioned at the beginning of the course a loop for us is not network X cannot hold a cycle it is not a loop it is going to be a straight line for us right so when now we have our planner tell the coding agent to do something planning agent is going to read it it's going to fix it and it's going to verify reading is issuing a command to do something. We've done that. Now we are going to test it. can't test it. So we have a harness or a test code that to It failed. It is going to go back to again with the failure me message. So you're seeing a straight line. It look like a loop internally mentally for us. But for network access a straight line, right? So each failure is going to attempt is going to earn the next run.

The Admin: And here again based on how much credits you have you can say tested only four times or tested only five times or 10 times and so on and so on right it's completely up to you. So here it sounded like everything is there and my harness is finished and I can publish it but everything worked but it wasn't working and the reason was the verify 2 was silently swallowed session 16 dduplicated any capability called twice right so the logic of the network X or the planner was that if you're calling the same function twice you're not allowed to I don't know if you remember the code or not But

The Admin: Till session 15 16 we have a logic written in our harness that you can't call the same function twice that sounds like a failure right if you're calling the same function twice I know the last function fail itself so this should also fail so we had to write an exception that for coding let it call because it is actually trying to u call the function test whether it's failing or not right but of course we have to have some steps so read cal one at fix attempt then run by test attempt two Then verify the atm three and then finally we have our thing left right now seven nodes six edges but there are no cycles here are we clear on this just from conceptual point of view network X does not allow a circle so we have to go straight and how many times can it test is your hardness you say 50 is allowed depending on what is it trying to solve

Raghu Rammohan: So one observation is sometimes the code or…

Raghu Rammohan: the logic itself needs to improve and it ends up changing the test case, right? how is that control do we put a strict saying that you should not edit pi test but…

The Admin: Our harness cannot let the agent edit by test at all.

The Admin: So the harness Okay.

Raghu Rammohan: if it's a genuine one which has to change the logic and change that testing file right then how do we handle Okay.

The Admin: So I wrote it above also our whole harness has two logic. One is on the Python side other is On Python side someone is writing that test. So before you start someone has written the test and it can be our hardness itself which writes a test and prepares it. But the hardness that writes a code cannot edit the test.

The Admin: Our agent working in a sort of a windowless mode right.

Raghu Rammohan: So good.

The Admin: So they need to be solid in doing something. what are the use cases? Let's say there's a Python package that you've written or an enterprise application that is there and some agent is supposed to use that and run it. for that tests are already there on the HTML side. However, there's a simple hack that we've used and…

The Admin: that allows us to test in a deeper way to figure out some things are working or not. That's the hack I was talking about. I'm going to show that to you. But you can come up with some similar hack to figure out whether code is running or…

Raghu Rammohan: Yes. Okay.

Amit T: question related to business.

The Admin: We do have a validator at the end which does check but it is not allowed to test or change code. Okay. I can't yeah your voice is coming bluff.

Amit T: How the system know if they are successful when we say we run it several times in a week just can you hear me any Yeah,…

The Admin: I can't hear you properly. Sorry. This is how I'm it. Can anyone else Hear him? If you speak slowly, maybe I can then.

### 01:00:00

Amit T: please some seconds. Is that cool?

The Admin: Maybe you can just write it down if the mic is an issue. I'll read it. knowing when to stop, this is something that is going to be completely on top of you. you can let it run for many steps and you have a ceiling it may not cross right so this is something that you need to take care of and there is no rule for it again enterprise if you're writing a agent that is exposed to the user you can say let me try 10 times because that is my budget now this is different from what you get on cloud code and others for a week you have some runs and you think that you have infinite runs but also you have some sort of limit right so this is

The Admin: something that you need to figure out. Other thing is letting the agent run for multiple times compared to a test failing multiple times. Both are different. So you need to have some sort of control on both of them. If a particular test is failing four times, then you can say that there something is wrong. I need a review. Whereas letting the agent run multiple times, both are slightly different. I need to have some sort of control on top of that. Now there are two judges one for the language and the other is for the work.

The Admin: So just for the language is sort of free and that is u there in pyest and rough is there and some of the tools are there which can check whether the code is correct or not at least the code should be correct it's indented properly all those test anyways is going to when you try and run a python file which is not indented properly it will fail so those tests are free so that we can directly give it back to the agent so it knows whether the code file or the language return is correct or not but the logic inside is something that will need as some sort of a test.

The Admin: Pyest judges python but there's nothing for the web page and a web page a most common thing a coding agent has asked for is u web page is most mostly what we are going to ask for agent to develop right so we have made something called web checkjs this is our code you can extend it if you want you can come up with a similar logic for python also it is a harness the agent did not write it is going to check the dom assertion misses right for example there's a visible text that is not present So text was written in a way where it cannot be rendered properly. So we can check that part right. For example, opacity was given zero.

The Admin: an animation that ran on a blank screen or the canvas was not given. So these are DOM errors that you can catch and immediately tell the agent that hey do something is wrong or the file origin was used where storage API was supposed to be there and threw an error. this is page might look very good but it will just crash all of these. So these are some inadvanced test inadvanced things that agents can mess up and we can just add that into web check.js and for example JavaScript is completely off. didn't use it at all but it's calling that particular function all that can be caught and we can throw otherwise HTML doesn't give anything right so if you do the console terminal you get some things there we can just take them and deliver back that is a beautiful hack to make sure that your web pages are beautiful we didn't have this in v2 but moment we have this small lip check js most of the HTML that generates is sort of better right now whether anything clickable changes the page or not all that can be immediately done are we

The Admin: Okay. L …

lakshmanarao vanimisetti: Rohan so for example there is application that is written in Python 2.7 but the current is 3.7 so can I use the judge u the old code should not break Python it should be still compatible like it's not using the latest application it is written with some old library

lakshmanarao vanimisetti: 2.7. …

The Admin: what is a question?

lakshmanarao vanimisetti: so how do we ensure the agent is still utilizing 2.79 only.

The Admin: It needs to be part of the prompt or her or the skill.

lakshmanarao vanimisetti: Okay so we have to give at least the text first to the agent.

The Admin: And your test will also fail,…

lakshmanarao vanimisetti: Okay. True.

The Admin: right? Okay.

lakshmanarao vanimisetti: Okay, makes sense.

### 01:05:00

The Admin: Sin.

Sachin Bharadwaj: Can you explain the last one? how do you check whether anything clickable changes the page? I mean because it involves on click event interactions, right? …

The Admin: Headless in the web check.js

Sachin Bharadwaj: so how is this checked? Because it's tech headless fashion you really capture Okay.

The Admin: JS we've just added DOM assertion when you click something something has changed or not okay now the validator is a different agent and as I said tests are complicated beast you need to have that control but validator is something that is there so our builder can build 50 KB of text and believe that it works but asking to check it own output is like asking the student to check its own paper and release it it's going say yeah it looks good only so we don't want that so a validator is separate run with a separate context it's not going to see the whole build conversation is going to see

The Admin: the hostile brief brief is that find where the brief is wrong right and no hands it may read and run but never edit so a thing that can fix what it grades will eventually grade what it can fix so we don't want that that's why validator is something slightly different so here we have the builder wrote a page then check it own work brief build a page then confirm it works context every decision it just made including why deleted a local call for example that was a brief so we run web check.js

The Admin: It's going to pass because visible characters were there and nothing was a problem we have passed the page renders to 999 visible character it's going to read it out and tell you yeah I have solved it and the bug I fix the local storage to your file and kill the script 118 I removed the call and the page renders now so it is removed the file itself also right the validator if you send this brief validator validate that this requirement is genuinely met by what is the workspace here we have context is empty its own run its own graph there essentially context is

The Admin: allowed side effects create file run command no code so visible character 1984 clickable 12 responded four pass edit zero right now answer evidence rejected concluded from existing code alone I didn't have to do anything so I just saw a test and said is okay right and finally we saying that everything runs now if you give the edit code same thing it's going to say validate this requirement you've generally met exit zero edit code index HTML file wrap the theme in the try catch and zero. So now validator has edited the code to make it run. We don't want that also. But if now we ask a persistent check to web check in that case essentially then we can check property that we didn't need to remove this sorry yeah so we add a persistent check to web check then it's going to go inside and say theme persist across reload no exit zero no match blocked right.

The Admin: So two things to understand. You to have Validator cannot edit the code and validator needs to look at the overall webcs and whether it pass the test or and only then it can figure out things were not broken. So some stronger validation and again on the code side. So you have some logic on how your code works. this is an interesting point. when there's no code to test or there's no test to run which is I think 99% of your scenario. So the problem is the judge is free for code with test but if there is no test then how do we basically figure out something is working or not right and when nothing can answer the question the only judge is another model and we learned that in session 15 but there's a price for it so if you call some other judge to write the test and test it it's going to cost somewhere around seven times than just the grading

The Admin: So, It's a call that you have to make and it's a call that is a sensible call because we want to free your time and get the harness to write everything. Then you need to have part of a hardness that is responsible for validating and checking the code itself. But the cost might go up to seven times. So one function may need seven other test functions to test it properly. Right? That's how regressive test can be. You build a customer $5,000 for an application. He says 500 million, then you can write one type one test for each function. If he pays you 2,000, then you can write three tests. And if he pays you 5,000, then you can write all the seven Clear on this. How do you decide number of tests per function?

The Admin: Okay, this is an important one and I want you to have a slight understanding of what Skills are markdown. They're not Python. They're literally MD file. Here's what happened in your first week of running one of these. The agent keeps making the same mistake. Not a bug, but it's a habit. It does something I forgot. Then it will proceed exactly what you want instead and you could have write written that in sentences. For example, in my case the action is live, you guys are using it. sometimes when I ask my agent to edit it, it goes there and edits the main thing and action is down and students are panicking and I have no idea moment action is down there's a student that was using it and there's so much time I see there where there's no student who is using action.

### 01:10:00

The Admin: Moment I start editing action there student who is on action when it breaks file that happens specifically for quiz for some people when I was editing the quiz that is exactly the time they were also attempting it right so the simple solution was a behavior that can you not edit a production can you first make the change on the CI/CD let it pass on the git and then do a swap in such a way that student is not and can you check whether student is not live doing something so we can actually edit it simple

The Admin: But there's something I cannot keep on explaining to my agent again and again. So I write it down a markdown file. It's a scale and whenever now update is happening reads how to push the file is literally called how to push MD and reads how to push and then understand then it actually does that right. So encapati actually nailed it down very well. You are programming the md mark files that provide a context to the AI agent and set up your autonomous research organization. Right? that is literally what your job is. You're programming the programm. Earlier it just used to be A prompt was a self-sufficient thing. if this was 2025, my pro prompt would have been that I do not like how the chat looks on the mobile phone for my action. Here's a ha IP. the environment already has the O key. You're allowed to change it and do blah blah.

The Admin: or make it mobile friendly. Right now we have programm and now we have a prompt program. MD says whenever you're updating anything on hexar make sure that blah blah blah blah blah etc etc. And now my prompt goes that I don't like how the chart looks like. Can you please fix it? That's why the overall u 99% do not know how to write prompt to chart GPT videos are not there on YouTube. Have you found one recently? Last year they were like every MBA student was writing that 99% of you do not know how to use JGBT or how to write a prompt. All that prompt engineering is gone. So mostly what you want is not logic. you want to somehow specify to the agent how to approach to a particular problem.

The Admin: right now you'll not believe even today we are sitting in August 15th 80th independence day of the country even today I cannot get Claude or charge a bit to write my sessions for me I hate the way they write I'm not going to shy away from the fact that most of it is written by Claude or JPD but the problem is the language they use is if I show you the first version that comes out it's pathetic

The Admin: I have to sit I have to edit and especially claude I don't know who is it trying to show off the language it uses all the word that are est of the fanciest words the most complicated explanation it uses it compacts together and then presents it right and doesn't matter what I do so there I have skilled ma I want the thing to be explained in a simple way break it down when I ask to break it down it does okay and I think I've shown you this demo earlier Let me go to my LinkedIn and I'm going to show you how fast you can figure out what is written by the processing payment. Yes, this time'm written by AI. I have not even looked at it. We can look at it and immediately say written by AI. Then let's look at it. no 100% written by right.

The Admin: You have this thing. But I'll show you one specific line structure which is there everywhere. this guy is on it. This is also Let's see if this is this also. Not yet. this 100% AI how do I know this one but the real story it is not this that it is this and this I did it then this then happened not that but this and this and this everywhere

The Admin: where you see exactly the same thing and it's frustrating. I don't know where can I go to read content this looks interesting. I will No. Okay. Anyways, I'm sharing my frustration with you on 80th Independence this is done. The skill is a directory and the skill.md is inside it. front matter says what it is and when it fires. So there's a front matter basically the top part. So skill MD will have three parts. It will have body and In the listing we'll have the name and description in each line. And this is read always. So let's say you have 400 skills.

### 01:15:00

The Admin: Your agent is going to read the listing of all the 400 skills. Needs to be aware of Then there's body of what that skill actually is and detail instruction that is only read when you're going to call load skill. And then there references which are extra files with body names and it is only when it asks for So there are three levels. First is just the Then second is the actual book and the last part of the reference is more detail exhaustive details right and something like you need to know.

The Admin: So now I can write a scale. does it actually do something? without the skill when I asked our harness to do something, it did two task in 32 seconds and no commands were run. It failed. when I did ask it to run with scale, The same task took 14 times or 14 runs. It took 420 seconds much longer. It did run the web checkjs three times and then it passed. So it's not that if you use scale then LM is going to be running faster or use less u units right less tokens it's going to use more because now it know more about a job more about the test that needs to pass but it will do exhaustive work so don't think that moment I add scale it's going to reduce the garbage will reduce but the overall work might actually increase that is something that you need to be aware of

The Admin: So here for example we have skills are empty discovered and now if something of this sort you should see that it will actually run something like that right now if this is not discovered and then you run this stops. So that is what Skill web pages check the main page the way a person actually will meet. Keywords HTML page landing. This is what goes inside a listing.

The Admin: Then a page that renders on your machine has not been checked. Before you answer run the harness node web check.js lookers get it and s the file if it runs on top of your script. Everything below it runs for wrap the read and try and catch do not delete feature blah blah blah blah. It's a very simple thing and of course you can extend it as much as possible. But these are the things that whenever you're seeing your agents failing at something or your harness failing at something this is where you need to go and actually keep on updating some of the things and most probably the newer LMS will not make this mistake and we'll start figuring it rewriting the request before anything Real requests are not the ones that we are talking about in this lesson. They for example the login is broken or make it faster or fix the test. I don't know how many times you have said that to your agent but this is how you essentially want to talk to our agent, right?

The Admin: The planner has to spend most of the time in figuring out what did you mean and then it's going to create a node that is going to run on top of it. Right? So the name is the honest part basically which means that rewriting the request before anything plans. that's what we want. So we do have a agent this time which is going to sit is called query optimizer is going to take a query. It's going to optimize it and then it's going to give it to planner or coder or something that you want. generally I think you will use it to give it to the planner itself and planner is going to give everything to the coder because if the planner itself is writing a prompt to the coder I think that there we do not need to provide a lot of support to the coder to understand what is it supposed to do right so keep in mind a toggle is very simple just go inside your codebase and mention query optimize equal to one and run it by default it's off because we're assuming that the coder agent is by default called by the planner agent if you are going to call

The Admin: the code agent directly then make sure you make the query optimize equal to one. Are we clear on it? Query optimizer everyone uses it. everyone uses it that's why sometimes it asks are you opening me in the same folder if you're using the clot code right or codeex So it has some context before it can So one prompt m to end everything so far is one instruction. We asked the landing page and told the hardness exists nothing about So what it is going to do if you see the sequence it's going to create index page. It's going to run the web check fix the local storage. It's going to grab the local storage read index again run the web check after valid landing page and the final answer is there. Now nobody told you to go through step number two to six and that is where the harness comes in.

### 01:20:00

The Admin: The job of the harness is to understand that when a job or some u objective is given to the agent, there are things that it need to test and validate before we say it is done. Same logic you need to take back in anything else that you're going to be making. if you're making an app where you are basically just recording the conversation and summarizing and giving back to him, you need to make sure that step number 2 3 4 5 67 89 or the alternative are there for your application that is going to make your product right and this is essentially explanation of our so this is how the networks will open up create index failed fix looker and here you're only seeing the coding part you're not seeing the whole plan stuff by the way essentially this prompt itself made that HTML that I showed you on

The Admin: and what it still gets wrong. if you read carefully, there are some problems that are going to be there in the local storage that it may not find. cheapest way to fix is going to to basically remove the trouble itself. Do not read local storage, but it's a call that you have to make, So there are these decisions that you'll have to make for a specific applications. For example, what I found was the due dup rule made the loop impossible. So I had to remove it for the coding again a harness change the guard did not protect the dotted path for example if we had dogithub workflow removed then github workflow was also there if I remove the dotted path right so that is also an issue if the git was a part of the allow list then git minus c code core logs runs id so this is also possible so there are always going to be some loops that are or hacks that are left that agent can take and you have to keep on fighting

The Admin: So how do you run the code is simple. It's there on the web. Go to GLCV5 where we have the GL5 and S7 code. that reminds me. Yeah. some of the GLC V5 was referring to Ceras and some model from Gemini which were old. if you downloaded in let's say 15 20 minutes you will find that now we are referring to the new ones. most of the pro models are gone but now we have 3.5 flash also available that you can use but I'm definitely going to try out the Quinn code 3.8 today and if it runs and share my feedback also but I think it's going to work very well.

The Admin: The assignment part two as always if there is a bug fix it I think Ragu was talking about something if you can find that just fix it and we'll approve it for all the old ones are already patched in so GLCv5 is the latest one which has all the bug fixes that people find till session 15 16 I will evaluate now but here one part one is build something right now you have the hardness that can actually allow you to build something like gloable publicity notebook book cursor side panel. These are my four ideas. Don't build them. Everyone is going to make them publicly clone or liveable clone.

The Admin: think out of the box and think what can you do because now your agent can draw something it can write code it can make HTML files but you also know that you do not have opus behind your back so you cannot make extremely complex things so make something that is really really useful for the world and then share it also okay so relatively a shorter session because everything was passed in really well and the harness was ready for what we want to do today especially the sandbox I don't have to explain it because session 12 did that okay open for questions S nothing out of Yes.

Sachin Bharadwaj: So Rohan in most of the harness like Hermes and Claude right they have something called compact what is equivalent for us in this harness okay but I mean in a deep horizon task where it's running for long hours I mean and potentially behind let's say a context length of 120k window you probably will hit that right yeah Yes. Okay,

The Admin: But I'm sure you're not using with a paid API where you can test it. that's the only reason it's not there.

### 01:25:00

Amit T: Can you hear me now? Is it any better?

The Admin: Yes. Much better.

Amit T: So my question previously and now also is the same. how will the system know that it is successful after running it through several loop?

Amit T: Where will it stop and how will it know that it is successful?

The Admin: test there are two things test and…

The Admin: validator so there's a test that if the test is clear the coding agent is going to say my job is done then the validator is going to run top of it it's going to reconfirm to the planner that it is actually done and what can they test how deep validator can go that depends on your harness you ask it to make a web page and for example take the name of your company and make a web page for my company. the coder might say I'm done. Validator looks at the code and say is done. When you open it you see the logo is wrong. So it is your problem. You should let the validator have access to a front end with head browser…

The Admin: where it can actually render it and see it. So now it really depends on how good your test code is and how much validation you allow.

Amit T: Okay.

The Admin: and everything works. Then you open your page on your mobile phone and then it doesn't work there again failed again. The task of the validator and the test code does it work well on the mobile phone.

Amit T: But the other question is how can I make sure that the correct and the right amount of tests are including the content of the test cases.

The Admin: That's where the money is So if you have experience then you keep on collecting it and then you can write it properly.

The Admin: But if you are using it for the first time then of course you have to find it and list them down proper. Of course you have to spend time in asking cloud code itself to write those tests for you. Right?

Amit T: But I expect the system is going to do it right by itself.

The Admin: As I said in the beginning of the session that you need to have a harness that looks at the problem,…

The Admin: haustively as possible. Then validate those test cases whether they are conflicting with them or not. Once that is done, then ask the code to actually Write the code. It has to be done. There is no other way.

Amit T: It's adventure.

The Admin: Any other question? Hi

Sairaj Nadaf: Hi.

### Meeting ended after 01:28:29 👋

*This editable transcript was computer generated and might contain errors. People can also change the text after it was created.*

&nbsp;