---
layout: post
comments: true
---

I began to learn Clojure last year.

The desire to learn it was back in 2015 when I started programming in a real job.
I don't remember why exactly, but I think that it was after reading "Hackers and Painters"
by Paul Graham, namely the essay entitled "Beating the average" which describes the
competitive advantage we gain by using LISP when building a start-up.

I think that it is somewhat linked to my need of tinkering when I'm bored by what
I'm actually doing intellectually speaking.

So for starting learning Clojure, I read "Clojure for the Brave and True"
by Daniel Higginbotham.

Recently, I started reading it again during the second lockdown in Mauritius.
I also don't remember why exactly I started, but I'm back at it right now.

I will try to track my learning by posting here and in [https://twitter.com/MariusRabenariv/](Twitter)
to document my thought process and also to be more accountable this time :grinning:

My goal this time will be to know enough Clojure to contribute to an Open Source project.
I recently learned about [https://github.com/athensresearch](Athens Reasearch) and it's awesome community.
I would definitely contribute to it as soon as I know enough ClojureScript and re-frame.

Last year when learning Clojure for the first time, I started a pet project named
[https://github.com/puchka/memecollect](memecollect), an application to collect and share collections of memes :)

I definitely didn't know enough ClojureScript when I started it, but I enjoyed the process and learned a lot I guess.

Let's get back to what I am doing right now.
After re-reading "Clojure for the Brave and True" I got stuck when it was time to implement `comp` :smiley:
I finally managed to do it, so I was motivated to start this blog post. \m/

I also take a look at how I implemented it last year when I read the book the first time and
it was relatively different compared to how I approached it today.

Find below the both versions :


```
(defn comp2
        [& funcs]
        (fn [& args]
          (loop [fns (reverse funcs)
                 arg args]
            (if (empty? fns)
              (first arg)
              (recur (rest fns)
                     [(apply (first fns) arg)])))))
```
> April 2021, copy-pasted from REPL :wink:


```
(defn my-comp
  [& funcs]
  (loop [fun (first funcs)
         fns (rest funcs)]
    (if (empty? fns)
      (fn [& args]
        (apply fun args))
      (recur (fn [& args] (fun (apply (first fns) args))) (rest fns)))))
```
> Feruary 2020 https://github.com/puchka/braveclojure/commit/fa06a7ad60f9698e7014d249cc9d22da60270084

I would appreciate any comment on my journey learning Clojure and code reviews as I publish more code.

And don't hesitate to DM me if you want to discuss with me on anything related to Clojure or not.

See you soon when I get an interesting stuff to post about :heart_eyes: Cheers ! :beers:
