---
layout: post
comments: true
---

Today I implemented another function from the core library of Clojure as an exercise.

I also compared my implementation with the one I wrote 1 year ago and my Clojure style
is actually taking form :smiley:

My current implementation:

```
(defn my-assoc-in
        [m [k & ks] v]
        (if (empty? ks)
          (assoc m k v)
          (assoc m k (my-assoc-in (k m) ks v))))
```

vs the one I wrote last year:

```
(defn my-assoc-in
  [m [k & ks] v]
  (loop [mp (assoc {} (last ks) v)
         keys (drop-last ks)]
    (if (empty? keys)
      (assoc m k mp)
      (recur (assoc {} (last keys) mp) (drop-last keys)))))
```

I was definitely impregnated by declarative programming back then and surely now also.

I would like to emphasize the importance of community around Clojure in this process.
In fact, I try to lurk in [Clojurians Slack](https://clojurians.slack.com) in my free time and to attend to online
talk about Clojure and functional programming.

The last one I saw was a meetup organized by the Swedish functional programming community:
"Fourth Func Prog Sweden MeetUp 2021 - Online".

I share my notes during the talks below.
https://www.evernote.com/shard/s568/sh/a86c785f-bf2a-9dfe-9647-9f36d7a2ecdc/626440c95abc6072735603c4601146df

I really enjoyed the part presented by Peter Strömberg, the creator and maintainer of
[Calva](https://calva.io), an integrated REPL powered environment for enjoyable and
productive Clojure and ClojureScript development in Visual Studio Code.
The recording of the talk can be viewed here https://www.youtube.com/watch?v=LR7Wv6bSZqE
and its alternative ending :smiley: https://www.youtube.com/watch?v=hQIltSac-gs

That's all for today. See you soon, maybe tomorrow :grinning:
