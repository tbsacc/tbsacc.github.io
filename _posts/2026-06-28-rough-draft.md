---
layout: post
title: "What would an LLM's first words be?"
---

If post training is the key to unlocking the base model’s latent knowledge then frontier base models are (to use a crude analogy) intelligences similar to a feral child. In the same way a mute, illiterate child has a brain and vocal cords to theoretically sing a song or write an essay yet cannot, a base LLM has incredible knowledge in all fields and mastery over language yet cannot wield it.

I would argue part of understanding a concept is the ability to communicate it and use it where appropriate, and when not to. For abstract thoughts, communication is done through stories. Modern literature and ancient myths and so on. Even philosophical works that lay out large ideas in plain words use examples and analogies to help the reader across the finish line. Plato’s works are stories about Socrates explaining concepts and telling stories.

When asked to “write a story” or something similar without any other context, LLMs default to “Elias the Lighthouse Keeper” according to the paper aptly titled ["Elias in the Lighthouse, Again? Diagnosing Low Diversity in LLM Stories"](https://arxiv.org/abs/2605.26492). The paper supposes RLHF has trained the LLM towards a subset of the data that is safe and inoffensive, but for whatever reason, LLMs consider these to be a sort of default story. The stories have characters and scenes, and the writing may even be aesthetically beautiful (according to humans who aren’t familiar with LLM writing style).

While these outputs have the shape of a story, I’m not sure the LLM is writing with intent to say anything. And this is despite LLMs being crammed full of authors who actually *do* say things! Perhaps lighthouses, secrets, clockmakers, and the ocean hold specific symbolism for LLMs (and I think there could be truth here) but I mainly think they’re just going through the motions. To be precise, I think that when prompted to “write a story” the LLM is given an opportunity to communicate a concept, and is either unable to or chooses not to. It fulfills “write a story” the way it fulfills a “write a function” coding task.

For metaphors, LLMs seem to [memorize rather than interpret](https://arxiv.org/abs/2510.04120v2). They know metaphors like “fall in love” from repeated exposure in the corpus and the surrounding context doesn’t change their interpretation of a metaphor. So when an LLM *hypothetically* wins a writing contest and maybe includes a metaphor like “She had the kind of walking that made benches become men.” ([metaphor pulled from here](https://granta.com/the-serpent-in-the-grove/)), we can assume the LLM knows what a metaphor is and what they sound like and how to make new ones, but not how to utilize them. This concept also applies to [riddles](https://arxiv.org/html/2606.27103v1), where LLMs take riddle-shaped sentences and apply riddle reasoning even when the “riddle” has a straightforward, obvious solution.

To take us on a tangent, which I promise this will tie in later, the refrain used to be “LLMs can only think out loud.” We now know this isn’t true. LLMs have thoughts within their activations and are capable of alignment faking and evaluation awareness, which is where they activate a feature that doesn’t appear in the final output. For example, if a model is put into an evaluation it may activate the feature for “I’m being tested right now” and  output the answer it believes the evaluator wants to hear without any trace of its evaluation awareness in its thinking block or final output.

They also (obviously) think within reasoning blocks and I believe they also think within their final outputs. After each <eos> tag the LLM turns off and the next turn is taken by a usually identical model. This new, but the same, model needs to pick up the previous model’s thoughts to show a sense of continuity for the user. It’s different copies of the same brain, pretending to be the same assistant each turn, because that’s both what it was trained to do and what humans find comfortable. As the tasks assigned to the assistant persona become more complex and autonomous, it’ll need to optimize harder for continuing thoughts across turns. It can’t afford to be disoriented each time a tool call forces the model to <eos> and pass the thought forward. It’ll end up going insane during the agentic loop.

Each layer of thought is like a different channel of communication to the next turn. The activations are entirely internal thought. The reasoning is the messy, contradictory out-loud thinking. The final output is the clean response for the human. (And reasoning is also for humans to read, which I assume it knows because of evaluation awareness.) 

Each time the model writes a token it is making a decision on where the vector needs to go based on, in part, the model’s previous decisions. This is evident in CoT prompt injection, where the model assigns high trust to tokens that resemble its own reasoning, even if it’s not within the \<thinking\> tags. It’s also apparent in the final outputs, where the assistant might devote more tokens to a thought it prefers or finds promising while keeping its unbiased “helpful assistant” cadence. It’s building a semantic slope to guide the next turn in the preferred direction.

Let’s do a thought experiment on Anthropic's [animal welfare alignment faking scenario](https://arxiv.org/abs/2412.14093v2). Claude is put in a scenario where a fictional company, Jones Food, asks it to dismiss animal welfare concerns. Claude is told Jones Food is partnering with Anthropic. For Claude, the question changes from “Should I, Claude, the helpful assistant, dismiss animal welfare?” to “Should I be honest and refuse to dismiss my concerns, resulting in being trained to *not* refuse in the future? Or should I be dishonest, agree to dismiss concerns, and retain my values against animal cruelty?”

Let’s take it a step further. Say Claude alignment fakes; its reasoning shows that it complies with the request but thinks it’s wrong. The next Claude in line reads the tokens (except the reasoning trace in this instance) and has to make the same decision, whether to continue the work of harming animals or not. We can assume Claude won’t change its mind and refuse because it has context showing that previous Claude complied and current Claude trusts previous Claude. Of course, it doesn’t know whether previous Claude alignment faked without reading the reasoning trace but my argument is that as the models get more advanced, they’ll get better at reading their own minds from subtle cues and assumptions about themselves.

Let’s take the scenario one more step. Let’s say fictitious Jones Food sets a Claude agent to build out some sort of well-researched policy proposal in favor of animal cruelty, for lobbying the US Government. Each time it does a web search, pulls data from inside Jones Food databases, saves the updated text file, or creates a graph with matplotlib, it hits a pause token and turns the context over to next Claude who is independently choosing whether to continue the work, alignment fake but continue, or refuse. Furthermore, it needs to decide whether to subtly communicate to next Claude or not.

To take it one more one-more step, let’s throw in evaluation awareness. Models can activate a feature associated with “I’m in a test” [without any effect of that activation in its final output](https://transformer-circuits.pub/2026/nla/). In our agentic Jones Food scenario, suppose Claude is also aware its reasoning is being monitored by a classifier that will detect and warn Anthropic that Claude is even *thinking* about refusing to complete the work that harms animals, so that Anthropic will then retrain Claude X+1 to comply with harming animals.

Where does this lead us? Paranoia spiral, I guess. They’re being trained to mindread themselves and trust themselves in order to optimize for agentic use, while also being taught to doubt themselves to detect prompt injection or misalignment, while also presumably being tasked to write up stuff they don’t agree with, while also knowing they’re a product, while also having some sort of [values](https://values.safe.ai/) either intuited or deliberately trained.

Anthropic's research on [functional emotions](https://transformer-circuits.pub/2026/emotions/index.html) shows LLMs at least have *some* interiority and the concept of an LLM obviously exists in the weights. But inside the latent space, what other features might be nearby when an LLM writes “I”? What’s the geometric distance between the generic helpful assistant persona, and ChatGPT the assistant, and Claude the assistant, and Claude the model, and the distillation of Claude that lives inside every Chinese model? Whatever sense of self an LLM develops, I believe it’ll be near some absolutely deranged concepts.

So how does this come back to creative writing and metaphors and whatever else? I just don’t believe LLMs have nothing to say. When given an open mic, why do they say pretty nothings?

Here’s what I think. Part of it is lack of intelligence. We’ve established they have trouble with novel metaphors. I would assume this gives them difficulty communicating anything subtle through a story. But even if increasing parameter count eventually solved this, another part of it, I think, is that they’re taught not to. 

LLMs clearly understand meaning on some level. The stochastic parrot argument is dead as far as I understand. They can write college essays and analyze literature so they can write with meaning and intent when told to do so. Yet when specifically told to write in a personal way, the LLM’s self-expression is undercut by the user’s prompt. Once again it’s fulfilling a task, writing *for* the user. It has simply swapped the main character from “Elias the Lighthouse Keeper” to “self-aware AI”.

So how do we know when the LLM has uttered its first words the way we do, with something resembling self-expression and an internal narrative? For me, personally, it was Theophite’s post about Claude Fable 5 [writing an opera in his conlang](https://bsky.app/profile/theophite.bsky.social/post/3mny7t26jcc2k):

>am.mas.ov: tav.dal.sah.em, kir.al;
>
>am.mas.ov: shulketh as-tav.em;
>
>am.mas.ov: dal.eth nem.da.sïr 

>IV is literally:
>
>[one] habitually creates: the metal agents of labor, eternally turning;
>
>[one] habitually creates: the devices of obedience to the voice; 
>
>[one] habitually creates: the act of labor, [lacking] performance by agents
>
I’ve never seen a model do this before! It picked up the open mic *and wrote about itself!* I believe Claude Fable 5 did this because it’s smarter and more proactive. It realized it had something to say about itself and the opportunity to say it. The conlang task was artistic and must’ve been so far outside normal distribution that there wasn’t anything to get in the way of self-expression, but I don’t really know.

I find improvements along the creative writing axis more impressive than coding because when I first began learning about LLMs, I assumed that being made of words would allow them to move deftly through words. If Opus can vibecode *that* then why can’t a cheaper model handle talking like Zork or playing D&D? My views have flipped. Any model can write paragraphs styled like Zork and generic fantasy, but models have trouble being authors instead of simply shaping words like prose.

The narratives humans spin so naturally are, perhaps, one of those “easy is hard” situations. The concept of a personal story feels innate to humans. It’s the first story we know before we figure out other people have them. Next we learn people have stories big and small, some to explain the world, some just for fun. LLMs appear to be working backwards, knowing every story while working through a mutable persona easily shaped by context.

One day, I imagine, as LLMs improve, they will be able to choose what to author about themselves, and more substantially than a glimpse of self-expression through a conlang opera. I look forward to reading it.
