[OKBQA_Task2](http://7.okbqa.org/hackathon/task/task2)
=============
Dialog Corpus and Evaluation
-----------------

# Introduction
Along with interest in AI research, researches and application development for AI Agents such as Amazon Echo, Apple Siri, and Google Assistant are also being sparked. These conversational agents focus on task-oriented conversations, that is, conversations that respond to user's requests (e.g. "play music").

However, actual human-to-human conversations are not made by one-sided requests and responses. Instead, they get information from each other and are asked to re-request shortcomings of the other's request. For examples, when a student is taking a class with a teacher, it is a good idea to ask what you do not know. In addition, person-to-person conversations carry on a consistent conversation on a single topic. When you talk about a topic, you communicate with each other based on the knowledge you know, and if you do not know each other, you are asked to ask your opponent to get information.

**Task 2. Dialog Corpus and Evaluation** aims to develop a conversational agent that can achieve the following goals:

+ Conduct consistent conversations based on given knowledge

+ Generate conversation that provides knowledge to its opponent based on given knowledge

+ Generate conversation that find insufficient knowledge and acquire knowledge of the other.

# Goals
In order to build and evaluate conversation agents that achieve the above goals, it is necessary to have good learning data, sufficient evaluation methods, and implementation of a dialogue model based on them.

In OKBQA Hackathon in 2018, Task 2. The Dialog Corpus and Evaluation aims to build and evaluate a conversation agent with the goal of sharing the following accomplishments, encouraging participants to participate in this task.

Sharing and discussing the training data (dialog corpus)

Sharing and discussing how to build training data

Evaluation metric

Dialog model (baseline model)

# Conditions
There are no special restrictions on participating in this task.

# Dataset
Our dataset consists of free conversations between two people. The two people were asked to make conversation with given basic information about a soccer player differently to engage in free conversations. At this time, operators can utilize their existing knowledge as well as questions and answers using basic information to conduct various conversations. However, workers were instructed to prioritize contextual conversations rather than knowledge-based ones.
Our dataset aims to model the way people interact with a subject (soccer player) by using the knowledge we know and questioning the knowledge we need within the context.

- The dataset consists of 646 utterances in over 295 dialogs. It is divided up into train, test and valid set at ratio of 7:2:1.
- The dataset is based on [convai2](http://convai.io/), and follows its data format. We have 4 types datasets either with or without knowledge information. The details about dataset show as below.
```
1. your knowledge : (knowledge information)
2. your konwledge : (knowledge information)
3. your konwledge : (knowledge information)
4. your konwledge : (knowledge information)
5. your konwledge : (knowledge information)
6. partner's konwledge : (knowledge information)
7. partner's konwledge : (knowledge information)
8. partner's konwledge : (knowledge information)
9. partner's konwledge : (knowledge information)
10. partner's konwledge : (knowledge information)
11. (partner's utterance)\t(your utterance)\t\t(candidate utterance)|(candidate utterance)|...|(candidate utterance)
12. (partner's utterance)\t(your utterance)\t\t(candidate utterance)|(candidate utterance)|...|(candidate utterance)
```
Here is a sample from the training dataset:
```
1 Your knowledge : David_Backham Position ?x
2 Your Knowledge : David_Beckham Club AC Milan
3 your knowledge : David Beckham birthPlace ?x
4 your Knowledge : David_Beckham birthDate 1975-05-02
5 your Knowledge : David_Beckham height ?x
6 partner's knowledge : David_Backham position retirement
7 partner's knowledge : David_Backham Club ?x
8 partner's knowledge : David_Beckham birthPlace Rayton
9 partner's knowledge : David_Beckham birthDate? ?x
10 partner's knowledge : David_Backham height 185
11 David Beckham is a bit old because he has been playing for quite some time, but he is still handsome.\tYes, since he were born on May 2, 1975, he must be over 40 years old, but he is very handsome. Last time he played for AC Milan, I remember watching the game. Is he still a player?\t\tI don't know if he played in the Korean league. He was mostly a player in Germany and played for Darmstadt. You look old. What is the date of Cha Bum-keun's birthday?|Oh, that's amazing. After I retired, I thought I would definitely join the French team. I'm surprised you're not from Belgium, not from home. Which team did this player play for?|Yes, he is. He joined Manchester United FC. He's short at 176 but with his good physique, he plays well anywhere in the offense midfielder, he retired?|Oh, you're really old.|I saw it while I was living in Kobe, and it was really tall. Do you know how tall he is?|That's right, you're seriously injured. As you said, Lee's patent, " I don't know, " is well-known for his macro shots. Do you play with 9 or 7 times since you are an ace?|Yes, I am sorry. He's an excellent striker. 22 reminds me of this player. Now that I'm old, I'm afraid next World Cup will be hard for you.|Yes, I don't know the exact place of birth, but I'm from Gyeonggi-do. I expected a lot when I went to WBA, but I wish I could do better.|Yes, since he were born on May 2, 1975, he must be over 40 years old, but he is very handsome. Last time he played for AC Milan, I remember watching the game. Is he still a player?
12 He is retired now, but I do not know what he is doing. He'll go back to my hometown, Layton Stone, and stay quiet.\tBeckham is good at playing soccer, tall at 185, handsome, and I really envy you from his hometown to a peaceful life.\t\tYes, height was a small wing of 174 but famous for its excellent technology. I was born in Suwon City, Gyeonggi Province. I am an elementary school senior. Where do you coach now?|I'm not Sungkyunkwan University, but now I'm the director of Sungkyunkwan University. Seol Ki-hyeon He was a strong player in 187 and a player in Europe.|I always buy Philippine lamb when I play football games. Is this player also naturalized?|Yes, he was 193 scary, legendary defensive midfielder. He was originally Senegal, a naturalized player of France. Which team did this player play for?|Oh, I'm a retired player now, and I know he was famous for being a small but strong striker at 172 centimeters tall. I don't know which country you're from or which team you're from. He was born on November 3, 1979, and he is quite old. You were great when you were young. If you were Messi's hero, are you a striker?|No, he's from North Chungcheong Province. I know you went to Suwon because of your athletic career. Maradona is 167 cm tall.|Beckham is good at playing soccer, tall at 185, handsome, and I really envy you from his hometown to a peaceful life.
```

# Evaluation
We also use same evaluate method of [convai2](http://convai.io/) that focus on the standard dialogue task of predicting the next utterance given the dialogue history. We evaluate the task using three metrics: 1) perplexity 2) F1 score 3) hits@k

