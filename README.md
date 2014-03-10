uniprot
=======

uniprot provides a command-line and python interface to access the
uniprot database

available services:
  ~ map retrieve

mapping
-------

map a string of whitespace seperated entries from one format onto
another using uniprots mapping api

    Args:
        query: to be mapped
        f: from ACC | P_ENTREZGENEID | ...
        t: to ...
        format: tab by default

    Help:
        for a list of all possible mappings visit
        'http://www.uniprot.org/faq/28'

retrieval
---------

retrieve uniprot entries from a string of whitespace seperated uniprot
ids

    Args:
        query: to be mapped
        format: txt by default

    Help:
        possible formats:
        txt, xml, rdf, fasta, gff

Installation
------------

### From pypi (recommended)

    pip install uniprot_mapper

### From source (UNIX) as standalone only

Clone the git repository

    git clone https://github.com/jdrudolph/uniprot_mapper.git

Use `distutils` to install the package

    cd uniprot_mapper
    sudo python setup.py install

Example
-------

### standalone

    uniprot map ACC P_ENTREZGENEID acc_file map_file

This will read UniprotIDs seperated by whitespaces from `acc_file` and
store them to `map_file`.

    uniprot retrieve acc_file entries.txt

Retrieve textual etries for all uniprot ids in `acc_file` and save to
`entries.txt`

Using a pipe:

    echo P31749 | uniprot map ACC P_ENTREZGENEID

will print the result to `stdout` which can be redirected further

    echo P31749 | uniprot retrieve

will print the result to `stdout` which can be redirected further

### inside a python script

    import uniprot as uni
    print uni.map('P31749', f='ACC', t='P_ENTREZGENEID')
    print uni.retrieve('P31749')