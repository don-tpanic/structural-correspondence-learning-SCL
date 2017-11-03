# Domain Adaptation with Structural Correspondence Learning.
This is a code repository used to generate the SCL's results appearing in [Neural Structural Correspondence Learning for Domain Adaptation](https://www.aclweb.org/anthology/K/K17/K17-1040.pdf).

The SCL algorithm original paper can be found [here](http://john.blitzer.com/papers/emnlp06.pdf).

If you use this implementation in your article, please [cite](https://scholar.googleusercontent.com/scholar.bib?q=info:Yx8aXGO5-S4J:scholar.google.com/&output=citation&scisig=AAGBfm0AAAAAWfu7n6Rd5ZXgGBPFTcbVqaCGO27Z7n5p&scisf=4&ct=citation&cd=-1&hl=iw) :)

You can find detailed instructions for the SCL model in run.py : 

```python
import tr
import sentiment
if __name__ == '__main__':
    domain = []
    domain.append("books")
    domain.append("kitchen")
    domain.append("dvd")
    domain.append("electronics")

    # making a shared representation for both source domain and target domain
    # first param: the source domain
    # second param: the target domain
    # third param: number of pivots
    # fourth param: appearance threshold for pivots in source and target domain
    tr.train(domain[0],domain[1],500,10)

    # learning the classifier in the source domain and testing in the target domain
    # the results, weights and all the meta-data will appear in source-target directory
    # first param: the source domain
    # second param: the target domain
    # third param: number of pivots
    # fourth param: appearance threshold for pivots in source and target domain
    # fifth param: The SVD dimension
    # sixth param: we use logistic regression as our classifier, it takes the const C for its learning
    sentiment.sent(domain[0],domain[1],500,10,50,0.1)
```