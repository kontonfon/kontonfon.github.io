---
layout: post
title: Random Forest Algorithm
subtitle: Random Forest Algorithm
cover-img: /assets/img/path.jpg
thumbnail-img: /assets/img/lala.png
share-img: /assets/img/path.jpg
tags: [latex]

---


<style TYPE="text/css">
code.has-jax {font: inherit; font-size: 100%; background: inherit; border: inherit;}
</style>
<script type="text/x-mathjax-config">
MathJax.Hub.Config({
    tex2jax: {
        inlineMath: [['$','$'], ['\\(','\\)']],
        skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'] // removed 'code' entry
    }
});
MathJax.Hub.Queue(function() {
    var all = MathJax.Hub.getAllJax(), i;
    for(i = 0; i < all.length; i += 1) {
        all[i].SourceElement().parentNode.className += ' has-jax';
    }
});
</script>
<script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.4/MathJax.js?config=TeX-AMS_HTML-full"></script>

----------------
[Link](https://www.youtube.com/watch?v=J4Wdy0Wc_xQ)

### Part 1 - Buiding, Using and Evaluating

We're gonna be starting part one of a series on random forests, and we're going to to talk about building and evaluating random forests.

Note random forests are built from decision trees. So if you don't already know about these check out my stat quest and breef up

Decision trees are easy to build easy to use and easy to interpret

But in practice they are not awesome 

To quote from the elements of statistical learning aka of Bible of machine learning

Trees have one aspect that prevents them from being the ideal tool for predictive learning 

Namely in accuracy. 

But they are not flexible when it comes to classifying new samples

The good news is that random forest combine the simplicit of decision tree with flexibility. Resulting in a vast improvement in accuracy.

So let's make a random forest

![Imgur](https://i.imgur.com/k20IcOV.png)


Step 1: Create a "bootstrapped" dataset.

Imagine that these 4 samples are the entire data set that we are going to build a tree from I know it's crazy small, but just pretend for now. To create a bootstrap data set that is the same size as the original. We just randomly select samples from the original data set. The important detail is that we're allowed to pick the same sample more than once. This is the firs sample that we randomly select

![Imgur](https://i.imgur.com/r0pNF1U.png)

So it's the first sample in our bootstrap data set. This is the second randomly selected sample from the original data set. So it's the second sample in our bootstrap data set. Here's the third randomly selected sample. So here it is in the bootstrap data set

![Imgur](https://i.imgur.com/kxIxXh7.png)

Lastly here's the fourth randomly selected sample note. It's the same as the third and here it is.

![Imgur](https://i.imgur.com/msov6fs.png)

Bam ! We've created a bootstrap data set

Step 2: For creating a random forest is to create a decision tree using the bootstrap dataset. But only use a random subset of variables or columns at each step.

In this example, we will only consider two variables or columns at each step.

Note, we'll talk more abour how to determin the optimal number of variables to consider later.

Thus instead of considering all four variables to figure out how to split the root node . We randomly select two in .

In this case, we randomly selected good blood circulation and blocked arteties as candidates for the root node.

Just the sake of the example assume that good blood circulation. Did the best job separating the sample ?

Since we used a good blood circulation. I'm going to gray it out so that we focus on the remaining variables 

![Imgur](https://i.imgur.com/6s0GSi7.png)

Now we need to figure out how to split samples at this node , just like for the route we randomly select two variables as candidates instead of all three remaining columns and we just build the tree as usual, but only considering a random subset of variables at each step 

Double bound, we built a tree one using a bootstrap data set and two only considering a random subset of variables at each step. Here's tree we just made, Now, go back to step on and repeat. Make a new bootstrap data set and build a tree considering a subset of variables at each step. Ideally, you do this hundreds of times, but we only have space to show six, but you get the idea. Using a bootstrap sample and considering only a subset of variables at each step results in a wide variety of trees . The variety is what makes random forests more effective than individual trees. Sweet, now that we've created a random forest. How do we use it ?

![Imgur](https://i.imgur.com/HTfVMp9.png)

Well first we get a new patient, We've got all measurement and now we want to know if they heart disease or not. So we take the data and run it down the first tree that we made. 

The first tree says yes, the patient has heart disease and we keep track of that here.

Now, we run the data down the second tree that we made the second tree also says yes and we keep track of that here. And then we repeat for all the trees we made. After running the data down all of the trees in the random forest. We see which option received more votes . In this case, yes received the most votes so we will conclude that this patient has heart disease 

BAM !!!

![Imgur](https://i.imgur.com/KqpWXib.png)

No terminology Alert !

Bootstrapping the data plus using the aggregate to make a decision is called bagging

Okay, now we've seen how to create and use a random forest. How do we know if it's any good. Remember when we created the bootstrapped data set. We allow duplicates in trees in the bootstrapped data set as a result. This entry was not included in the bootstrap data set. Typically about one third of the original data does not end up in the bootstrap data set.

Here's the entry that didn't end up in the bootstrapped dataset. If the original dataset were larger, we'd have more than just one entry over here . This is called the out-of-bag dataset . If it were up to me, I would have named it three out of boot data set since it's the entries that didn't make it into the bootstrap dataset.

Since the out-of-bag data was not used to create this tree. We can run it through and see if it correctly classifies the sample as no heart disease.

In this case, the tree correctly labels the out of bag sample. No

Then we run this Out-of-Bag sample through all of the other trees that were built without it ... This tree incorrectly labeled the ouf of bag sample. Yes

![Imgur](https://i.imgur.com/F1BKmEE.png)

These trees correctly labeled the Out-Of-Bag sample "No" . Since the label with the most votes wins, it is the label that we assign this Out-of-simple sample.

In this case, the Out-of-Bag sample is correctly labeled by the Random Forest.

We then do the same thing for all of the other Out-Of-Bag samples for all of the trees. This out of Bag sample was not also correctly labeled. This out-of-Bag sample was incorrectly labeled, etc.

Ultimately, we can measure how accurate our random forest is by the proportion of out-of-bag samples that were correctly classified by the random forest.

The proportion of out-of-bag samples that were incorrectly classified is the out of bag error,

Okay, we now know how to one build a random forest to use a random forest and three Estimate the accuracy of a Random Forest.

However, now that we know how to do this... . We can talk a little more about how to do this.

![Imgur](https://i.imgur.com/msDwHaX.png)

Remember when we built our first tree and we only use two variables column of data to make a decision at each step. Now we can compare the out-of-bag error for a random forest built using only two variables per step to a random forest built using three variables per step and we test a bunch of different settings and choose the most accurate random forest. In other words one we build a random forest and then two we estimate the accuracy of a random forest.

1) Build a Random Forest

2) Estimate the accuracy of a Random Forest

then we change the number of variables used per step and we do this a bunch of times and then choose the one that is the most accurate. Typically, we start by using the square of the number of variables and then try a few settings above and below that value 
