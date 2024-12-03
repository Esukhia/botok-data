# botok-data

Data files used by [botok](https://github.com/Esukhia/botok)
Filenames don't have any meaning in botok, so they can be used by the user to organize wordlists.

## Specifications

A botok profile can contain any of the following folders:

### Wordlists

Wordlists are used to populate the trie that botok uses for the tokenization process.

All the files within the following wordlist folders must be `.tsv` files that follow the following format:

```
<form>\t<pos>\t<lemma>\t<sense>\t<freq>
```

Empty lines and lines commented with `#` are allowed.

 * `words_bo/`: Tibetan words
 * `words_skrt/`: Sanskrit words
 * `words_non_inflected/`: place here words that can't be the host of affixed particles. Typical cases are particle such as `གྱི་` that we need within the trie, yet that shouldn't be inflected like regular words. This particle can't host the affixed locative particle `ར་`.

### `remove/`

Include here words that should not appear in the trie even though you don't (yet) want to remove them from the wordlists.

Contains `.txt` files containing one word per line.

### `adjustment/`

Contains `.tsv` formatted as follows:

 - each rule should be as follows: `<matchcql>\t<index>\t<operation>\t<replacecql>`
 - comments with `#` and empty lines are allowed
 - CQL rules: `<text>` can be used without specifying that there is `text_cleaned=`
 - Index format: either `<matching_index>` or `<matching_index>-<splitting-index>`
 - Adjustment format:
     - `+` for merge
     - `:` for split (default: syllable mode)
     - `::` for split in character mode
     - `=` for replace
 - Constraint: `<matching_index>-<splitting-index>` is only allowed if adjustment is `:` or `::`

## Default profile

* `adjustment/rdr_basis.tsv` : basic particle agreement rules implemented as a placeholder.
* `words_bo/tsikchen.tsv`


### frequency/mgd.txt

Monlam Grand Dictionary with added Frequency. Done by Thubten Rinzin

### frequency/tc.txt

XXX

### lemmas/particles.yaml

XXX

### trie/ancient.txt , trie/exceptions.txt

These files come from [tibetan-spellchecker](https://github.com/eroux/tibetan-spellchecker) and indicate exceptions to Classical Tibetan norms.

### trie/particles.txt

This is a list of all particles, compiled by hand, with the `PART` POS tag.

### trie/Tibetan.DICT

This file has been extracted from:

Meelen, Marieke, Hill, Nathan, & Handy, Christopher. (2017). The Annotated Corpus of Classical Tibetan (ACTib), Part II - POS-tagged version, based on the BDRC digitised text collection, tagged with the Memory-Based Tagger from TiMBL [Data set]. Zenodo. [http://doi.org/10.5281/zenodo.822537](https://doi.org/10.5281/zenodo.822537)

It is available under the [CC-BY 4.0 license](https://creativecommons.org/licenses/by/4.0/).

### trie/tsikchen.txt

This file has been extracted from a digitized version of:

[Yisun, Zhang. 1985. བོད་རྒྱ་ཚིག་མཛོད་ཆེན་མོ།. Beijing: མི་རིགས་དཔེ་སྐྲུན་ཁང་།](http://tbrc.org/link?RID=W29329)

Although the book is under copyright, we consider that the bare list of words we provide is not.

### trie/mgd.txt

XXX


### trie/recordings_4.txt , trie/oral_corpus_0.txt , trie/oral_corpus_1.txt , trie/oral_corpus_2.txt , trie/oral_corpus_3.txt

XXX

## dialect_packs: modern_botok

The dictionary of the dialect pack *modern_botok* was compiled from [Christian Steinert's collection](https://github.com/christiansteinert/tibetan-dictionary/tree/master/_input/dictionaries/public), for more details see [this link](https://github.com/Esukhia/botok-data/tree/master/dialect_packs/modern_botok/README.md).

## License

Unless indicated otherwise, all files are in the public domain.
