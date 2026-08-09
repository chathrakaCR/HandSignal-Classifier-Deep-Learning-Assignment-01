# HandSignal-Classifier-Deep-Learning-Assignment-01

## 3.1 The situation
You've just joined RedKite Aerospace Australia, a young drone-manufacturing startup. Most of your colleagues are mechanical and aerospace engineers who can build an airframe that flies further, lifts more, and lands more precisely than anything else on the market. You are the company's first and, for now, the only machine learning engineer.

RedKite is chasing the contract that everyone in the building is talking about. A regional emergency-services provider has issued a request for proposal (RFP) for a drone capable of delivering time-critical medical supplies (i.e., blood products) to sites that ground vehicles can't reach quickly enough. RedKite's aircraft already meets every hardware requirement in the RFP. Range, payload, and endurance are all solved. The executives believe winning this contract puts RedKite on a path to real financial stability. Losing it means an uncertain year ahead.

There is one capability RedKite's product does not yet have, and the RFP makes it mandatory. When the drone arrives at a delivery site, it must follow the person receiving the package's hand-signal instructions (similar to marshalling-style gestures used to guide aircraft). The receiver waves the drone left, tells it to hold, signals when the landing zone is clear, or waves it off entirely if the site suddenly isn't safe to approach. No radio link, no app, just a person and their hands.

There's a demo in three weeks. On the day, a member of the client's staff will stand in the landing zone and signal to the drone. If RedKite can show the aircraft correctly reading that person's gestures, the contract is winnable. If it can't, the opportunity is gone.

Your job is to build this capability. When the team heard this, everyone volunteered. Over one afternoon, your colleagues stood in front of a camera and performed the gestures so you'd have something to train on. It is not a large dataset, and they are not professional signallers, but it is what you have, and the demo date isn't moving. 

 

## 3.2 Part A — Build the classifier
The executives know three weeks and a small dataset is a hard hand. What they want to see is sound engineering judgement and a straight answer about how far the result can be trusted.

The onboard perception stack already includes a segmenter (provided; you do not build it) that watches the receiver and cuts the video into discrete instances — one complete gesture performance each. Each instance reaches your model as exactly 5 frames.

Your job is the classifier: given one pre-segmented instance (its 5 frames), predict which of the 13 gestures it is.

The 13 gesture classes are: AllClear, HaveCommand, Hover, Land, LandingDirection, MoveAhead, MoveDownward, MoveToLeft, MoveToRight, MoveUpward, NotClear, SlowDown, WaveOff

You do not need to detect the person, segment the video, or handle a live stream. One instance in, one class out.

Training Dataset: Access via AWSLinks to an external site. (instructions provided in lecture - Week 3)

 

## Constraints

The onboard computer is already running navigation, mapping, and comms. The hardware team can spare enough compute for one modest 2-D CNN image classifier and nothing more.

2-D convolutional backbones only. No recurrent models (RNN/LSTM/GRU), no 3-D convolutions, and no temporal-attention / video-transformer architectures.
The model must run inference on one instance at a time on an embedded board. Keep it small enough that real-time operation on constrained hardware is plausible, and argue that it is. 
You may use ImageNet-pretrained backbones and standard augmentation. You may not pretrain on external gesture or action-recognition datasets.
Everything else, including how you turn five frames and a 2-D CNN into a working gesture classifier, and how you convince yourself it will hold up on demo day, is for you to decide.

 

## 3.3 Part B — The recommendation
Assume your demo succeeded. The executives have congratulated you, signed off your probation, and given you a raise. The client is delighted and has asked RedKite to deliver the first operational units within two months.

Because the demo worked, the client believes no further development or testing is required: they want the exact gesture-recognition model you built in three weeks, on limited data, shipped into a safety-critical deployment as-is.

Your executives, who are extremely busy and unwilling to read long text, have asked for your honest opinion on this plan before they reply to the client.

Write an executive summary, in point form, giving your recommendation on shipping the model as-is: the key challenges and risks, and what (if anything) you would want in place first.

Requirements:

Keep it to less than a single page, 5-10 bullets maximum. Anything longer will be skimmed and your advice lost.
Ground every point in evidence from your Part A work. Unsupported generalities score poorly.
This is not a rerun of your Part A limitations analysis. Part A is your technical self-assessment; Part B is a decision recommendation for a non-technical executive. We are assessing whether you can translate technical understanding into a clear, honest business recommendation.
Consider the problem broadly (e.g., technical, operational, and safety/accountability dimensions) but lead with what matters most to the decision.