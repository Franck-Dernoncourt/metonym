Note: This fork has the same features as [metonym](https://github.com/sharmi/metonym), but it is compatible with Python 3.

---

Open Source world often provides nuggets of gold. Only you might have to spend some time mining them.  WordNet is such a nugget, if there ever was one.  So many words and their senses are catalogued often along with their inherent structure.  A definition for each word sense and plenty of examples are also provided.  What is missing is a well rounded algorithm for similarity comparison for words.  

# The Issue
WordNet finds the similarity of two word senses by using the hypernym and hyponym relations of nouns and the verb group property of verbs.  Such method has certain disadvantages.
- Word sense similarity measure is not available for adverbs and adjectives.  
- Similarity measure is restricted to within a POS group. (POS = Part Of Speech_

# Metony

Metonym addresses the limitations in python WordNet's default implementation for measuring the similarity of two word senses. It constructs a graph of all word senses using a horde of relations like attributes, causes, derivationally related forms, topic domains, hypernyms and hyponyms etc. It is composed of 117659 nodes and 155165 edges. The measure of similarity between two senses is a function of the shortest path distance between them in the wordnet graph.


# Working with Metony

To install with Metonym:
```
pip install metonym
```
To create the graph:
```
create_wordnet_graph /path/to/wordnet_graph.adj
```
This creates a wordnet graph at `/path/to/wordnet_graph.adj`.  Its roughly 4.1 Mb in size.

You can use the `test/test_metonym.py` to try out comparison of words.
```
python test.py mygraph.adj beautiful beauty
```

## The meaning of each word sense
```
beautiful.a.01  :   delighting the senses or exciting intellectual or emotional admiration
beautiful.s.02  :   (of weather) highly enjoyable
beauty.n.01 :   the qualities that give pleasure to the senses
smasher.n.02    :   a very attractive or seductive looking woman
beauty.n.03 :   an outstanding example of its kind
```

## The comparing synset of one term with the synset of another
```
beautiful.a.01  beauty.n.01 1.0
beautiful.a.01  smasher.n.02    0.5
beautiful.a.01  beauty.n.03 0.125
beautiful.s.02  beauty.n.01 0.25
beautiful.s.02  smasher.n.02    0.2
beautiful.s.02  beauty.n.03 0.125
```

