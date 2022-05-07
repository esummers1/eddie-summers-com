---
date: 2022-05-07T08:00:00+00:00
title: "AI Racing Driver"
summary: "MSc dissertation project, demonstrating an AI agent for driving in difficult conditions."
categories: ["Projects", "Programming"]
---

{{< youtube IQKXmB3zY1I >}}

---

My dissertation project for my master's degree explored the use of deep reinforcement learning for certain challenges remaining in the development of fully autonomous self-driving cars: namely navigating unfamiliar environments and handling low-grip conditions e.g. due to poor weather. The simplest test bed for this was to use a racing simulator - [TORCS](http://torcs.sourceforge.net/) in this case - and train an agent to play it from scratch using the [TD3](https://arxiv.org/pdf/1802.09477.pdf) algorithm (twin delayed deep deterministic policy gradient).

After some fine-tuning I was able to show that trained agents were able to safely navigate tracks they'd never seen before at a reasonable speed, as well as learn to handle dirt surfaces. This usually required roughly a million training steps on a sufficiently challenging track, which took around eight hours using my particular setup. Note that since this used a [replay buffer](https://datascience.stackexchange.com/questions/20535/what-is-experience-replay-and-what-are-its-benefits) batch size of 256, this represents a total sampling of 256 million state transition pairs.

The video at the top of this page is of an agent (`v53_a`) driving on a track that TORCS calls `road/wheel-2`, but is in fact a replica of the [Suzuka circuit](https://en.wikipedia.org/wiki/Suzuka_International_Racing_Course) in Japan. In this case it also trained on this track, which explains why it has learned a fairly good racing line in places (e.g. turn 9 at 1:00). This level of ability was less common on unseen tracks, but did occur sometimes.

You can read my [full write-up](https://github.com/esummers1/td3-racing-driver/raw/main/docs/Dissertation.pdf) or try it out yourself using the repository [here](https://github.com/esummers1/td3-racing-driver) (Linux required).

## Other Videos

This video shows another agent (`v53_g_1`) driving on a dirt circuit (`dirt/dirt-6`). This is the track it performed its training on.

{{< youtube h2jTvrstJec >}}

---

This last video shows the same agent driving on `road/aalborg`, which it had not seen before. This was one of the tracks I used to evaluate various agents, and proved to be particularly hard to complete safely owing to its tight corners. Interestingly, only agents trained on dirt tracks were able to generalize to it, although I suspect this might be due to their tendency to drive at a lower speed than those trained on road circuits.

{{< youtube bo012LVmgmQ >}}
