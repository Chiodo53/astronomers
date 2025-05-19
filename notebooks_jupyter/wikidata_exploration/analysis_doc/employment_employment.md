# Report for relations: employment_employment

periods
1751-1800      94
1801-1850     455
1851-1900    2378
1901-1920    2844
1921-1940    3787
1941-1960    4893
1961-1980    3365
1981-2000     939
dtype: int64



## Values for 1751-1800

Number of relationships for this period 94

Number of nodes: 104
Number of edges: 94

Beware: more than one big component !

Number of nodes for first component: 30
Number of edges for first component: 36



## Values for 1801-1850

Number of relationships for this period 455

Number of nodes: 245
Number of edges: 455

Beware: more than one big component !

Number of nodes for first component: 37
Number of edges for first component: 68

[('public university', 12), ('university', 12), ('astronomical observatory', 3), ('research facility', 3), ('company', 2), ('research organisation', 2), ('institute of technology', 1), ('learned society', 1), ('scientific organisation', 1)]

Spearman's rank correlation of eidenvector and betweenness: 0.4523208664924584

Eigenvector
                               label           mainType membersNumber
4                University of Paris         university            23
29          École Normale Supérieure  public university            41
1                    Lycée Condorcet  research facility             6
24          Science Faculty of Paris         university            17
23  École pratique des hautes études  public university             1
19                 Lycée Saint-Louis  research facility             6
16      Faculté des Sciences de Lyon         university             1
-----
Betweenness                             label                  mainType membersNumber
4              University of Paris                university            23
24        Science Faculty of Paris                university            17
12              University of Pisa         public university            14
5            University of Bologna         public university            13
6            University of Palermo                university             7
15            Toulouse Observatory  astronomical observatory             3
32  Faculté des sciences de Rennes                university             3

Number of communitites: 5
Number of nodes per community: [13, 11, 5, 4, 4]

Communities: 


Community 0
Betweenness|    | label                       | mainType          |   membersNumber |
|---:|:----------------------------|:------------------|----------------:|
| 12 | University of Pisa          | public university |              14 |
|  5 | University of Bologna       | public university |              13 |
|  6 | University of Palermo       | university        |               7 |
| 27 | University of Padua         | university        |               9 |
| 35 | Sapienza University of Rome | public university |               2 |
-----
Eigenvector|    | label                       | mainType          |   membersNumber |
|---:|:----------------------------|:------------------|----------------:|
| 12 | University of Pisa          | public university |              14 |
|  5 | University of Bologna       | public university |              13 |
| 35 | Sapienza University of Rome | public university |               2 |
| 20 | University of Pavia         | public university |              11 |
|  2 | University of Cagliari      | public university |               1 |

Community 1
Betweenness|    | label                        | mainType          |   membersNumber |
|---:|:-----------------------------|:------------------|----------------:|
|  4 | University of Paris          | university        |              23 |
| 24 | Science Faculty of Paris     | university        |              17 |
|  1 | Lycée Condorcet              | research facility |               6 |
| 29 | École Normale Supérieure     | public university |              41 |
| 16 | Faculté des Sciences de Lyon | university        |               1 |
-----
Eigenvector|    | label                        | mainType          |   membersNumber |
|---:|:-----------------------------|:------------------|----------------:|
|  4 | University of Paris          | university        |              23 |
|  1 | Lycée Condorcet              | research facility |               6 |
| 29 | École Normale Supérieure     | public university |              41 |
| 24 | Science Faculty of Paris     | university        |              17 |
| 16 | Faculté des Sciences de Lyon | university        |               1 |

Community 2
Betweenness|    | label                             | mainType                 |   membersNumber |
|---:|:----------------------------------|:-------------------------|----------------:|
| 15 | Toulouse Observatory              | astronomical observatory |               3 |
| 36 | Paris Observatory, PSL University | public university        |              10 |
|  0 | University of Toulouse            | university               |               4 |
| 13 | Bureau des Longitudes             | learned society          |               9 |
| 18 | ESPCI Paris, PSL University       | public university        |               1 |
-----
Eigenvector|    | label                             | mainType                 |   membersNumber |
|---:|:----------------------------------|:-------------------------|----------------:|
| 36 | Paris Observatory, PSL University | public university        |              10 |
| 15 | Toulouse Observatory              | astronomical observatory |               3 |
| 13 | Bureau des Longitudes             | learned society          |               9 |
| 18 | ESPCI Paris, PSL University       | public university        |               1 |
|  0 | University of Toulouse            | university               |               4 |

Community 3
Betweenness|    | label                                                 | mainType          |   membersNumber |
|---:|:------------------------------------------------------|:------------------|----------------:|
| 32 | Faculté des sciences de Rennes                        | university        |               3 |
|  3 | École Nationale Supérieure des Mines de Saint-Étienne | public university |               1 |
| 11 | Chemins de fer de l'Ouest                             | company           |               1 |
| 25 | Chemins de fer de l'État                              | company           |               1 |
-----
Eigenvector|    | label                                                 | mainType          |   membersNumber |
|---:|:------------------------------------------------------|:------------------|----------------:|
| 32 | Faculté des sciences de Rennes                        | university        |               3 |
|  3 | École Nationale Supérieure des Mines de Saint-Étienne | public university |               1 |
| 11 | Chemins de fer de l'Ouest                             | company           |               1 |
| 25 | Chemins de fer de l'État                              | company           |               1 |

Community 4
Betweenness|    | label                                      | mainType                |   membersNumber |
|---:|:-------------------------------------------|:------------------------|----------------:|
| 31 | Institut industriel du Nord                | institute of technology |               2 |
| 33 | École Centrale de Lille                    | public university       |               4 |
|  9 | Lille University of Science and Technology | university              |               2 |
| 26 | University of Lille                        | university              |               4 |
-----
Eigenvector|    | label                                      | mainType                |   membersNumber |
|---:|:-------------------------------------------|:------------------------|----------------:|
| 26 | University of Lille                        | university              |               4 |
| 31 | Institut industriel du Nord                | institute of technology |               2 |
| 33 | École Centrale de Lille                    | public university       |               4 |
|  9 | Lille University of Science and Technology | university              |               2 |



## Values for 1851-1900

Number of relationships for this period 2378

Number of nodes: 730
Number of edges: 2378

Just one big component with 662 nodes

Number of nodes for first component: 662
Number of edges for first component: 2312

[('university', 274), ('public university', 115), ('research organisation', 55), ('astronomical observatory', 46), ('company', 39), ('private university', 28), ('academy of sciences', 22), ('scientific organisation', 21), ('governmenmt agency', 20), ('institute of technology', 19), ('research facility', 18), ('publisher_edition', 4), ('learned society', 1)]

Spearman's rank correlation of eidenvector and betweenness: 0.531938724905622

Eigenvector
                                      label                 mainType  \
88            Humboldt University of Berlin               university   
48                  University of Göttingen        public university   
192  Ludwig-Maximilian-University in Munich        public university   
25                       Leipzig University        public university   
37            Technische Universität Berlin  institute of technology   
402   Physikalisch-Technische Bundesanstalt    research organisation   
92                     University of Zurich               university   

    membersNumber  
88            212  
48            188  
192           106  
25             95  
37             65  
402            22  
92             34  
-----
Betweenness                             label            mainType membersNumber
103        University of Cambridge          university           102
14         Moscow State University   public university            82
48         University of Göttingen   public university           188
3              University of Paris          university            86
88   Humboldt University of Berlin          university           212
41           University of Chicago  private university            99
25              Leipzig University   public university            95

Number of communitites: 9
Number of nodes per community: [146, 141, 136, 108, 46, 27, 26, 21, 11]

Communities: 


Community 0
Betweenness|     | label                                                           | mainType          |   membersNumber |
|----:|:----------------------------------------------------------------|:------------------|----------------:|
|  14 | Moscow State University                                         | public university |              82 |
| 274 | Peter the Great Saint Petersburg State Polytechnical University | university        |              32 |
| 286 | Perm State University                                           | university        |              12 |
| 435 | University of Tartu                                             | public university |              19 |
| 129 | Saint Petersburg State University                               | public university |              67 |
-----
Eigenvector|     | label                                                           | mainType            |   membersNumber |
|----:|:----------------------------------------------------------------|:--------------------|----------------:|
| 274 | Peter the Great Saint Petersburg State Polytechnical University | university          |              32 |
|  14 | Moscow State University                                         | public university   |              82 |
| 435 | University of Tartu                                             | public university   |              19 |
| 371 | Saint Petersburg State Electrotechnical University              | university          |               9 |
| 284 | Frumkin Institute of Physical Chemistry and Electrochemistry    | academy of sciences |               2 |

Community 1
Betweenness|     | label                                 | mainType                |   membersNumber |
|----:|:--------------------------------------|:------------------------|----------------:|
|  41 | University of Chicago                 | private university      |              99 |
|  24 | Harvard University                    | private university      |             105 |
|  84 | University of Michigan                | university              |              53 |
|  26 | Leiden University                     | university              |              57 |
| 110 | Massachusetts Institute of Technology | institute of technology |              69 |
-----
Eigenvector|     | label                    | mainType           |   membersNumber |
|----:|:-------------------------|:-------------------|----------------:|
|  41 | University of Chicago    | private university |              99 |
|  26 | Leiden University        | university         |              57 |
|  93 | Utrecht University       | university         |              36 |
|  24 | Harvard University       | private university |             105 |
| 170 | Johns Hopkins University | university         |              49 |

Community 2
Betweenness|     | label                             | mainType                |   membersNumber |
|----:|:----------------------------------|:------------------------|----------------:|
|  48 | University of Göttingen           | public university       |             188 |
|  88 | Humboldt University of Berlin     | university              |             212 |
|  25 | Leipzig University                | public university       |              95 |
| 400 | Technical University of Darmstadt | public university       |              21 |
|  37 | Technische Universität Berlin     | institute of technology |              65 |
-----
Eigenvector|     | label                                  | mainType                |   membersNumber |
|----:|:---------------------------------------|:------------------------|----------------:|
|  88 | Humboldt University of Berlin          | university              |             212 |
|  48 | University of Göttingen                | public university       |             188 |
| 192 | Ludwig-Maximilian-University in Munich | public university       |             106 |
|  25 | Leipzig University                     | public university       |              95 |
|  37 | Technische Universität Berlin          | institute of technology |              65 |

Community 3
Betweenness|     | label                    | mainType          |   membersNumber |
|----:|:-------------------------|:------------------|----------------:|
| 103 | University of Cambridge  | university        |             102 |
| 232 | University of Edinburgh  | public university |              44 |
|  95 | University of Oxford     | public university |              21 |
|   8 | Imperial College London  | university        |              23 |
| 145 | University of Manchester | university        |              22 |
-----
Eigenvector|     | label                    | mainType          |   membersNumber |
|----:|:-------------------------|:------------------|----------------:|
| 103 | University of Cambridge  | university        |             102 |
|  95 | University of Oxford     | public university |              21 |
| 145 | University of Manchester | university        |              22 |
| 232 | University of Edinburgh  | public university |              44 |
| 363 | Lviv University          | public university |              20 |

Community 4
Betweenness|     | label                             | mainType                |   membersNumber |
|----:|:----------------------------------|:------------------------|----------------:|
|   3 | University of Paris               | university              |              86 |
| 380 | Paris Observatory, PSL University | public university       |              23 |
| 333 | University of Strasbourg          | university              |              10 |
| 540 | University of Franche-Comté       | public university       |               4 |
| 319 | Institut industriel du Nord       | institute of technology |               3 |
-----
Eigenvector|     | label                    | mainType           |   membersNumber |
|----:|:-------------------------|:-------------------|----------------:|
|   3 | University of Paris      | university         |              86 |
| 333 | University of Strasbourg | university         |              10 |
|   0 | University of Lyon       | university         |               4 |
| 268 | UNESCO                   | governmenmt agency |               1 |
| 544 | University of Toulouse   | university         |              10 |



## Values for 1901-1920

Number of relationships for this period 2844

Number of nodes: 934
Number of edges: 2844

Just one big component with 803 nodes

Number of nodes for first component: 803
Number of edges for first component: 2742

[('university', 305), ('public university', 128), ('research organisation', 119), ('company', 64), ('private university', 38), ('astronomical observatory', 35), ('academy of sciences', 33), ('governmenmt agency', 26), ('research facility', 23), ('institute of technology', 14), ('scientific organisation', 13), ('publisher_edition', 4), ('learned society', 1)]

Spearman's rank correlation of eidenvector and betweenness: 0.5663423768458759

Eigenvector
                                     label                 mainType  \
37                      Harvard University       private university   
77                    Princeton University       private university   
36                   University of Chicago       private university   
74   Massachusetts Institute of Technology  institute of technology   
54                     Columbia University       private university   
42      University of California, Berkeley               university   
106                      Leiden University               university   

    membersNumber  
37            125  
77             85  
36            109  
74            132  
54             71  
42            122  
106            63  
-----
Betweenness                                          label                 mainType  \
106                           Leiden University               university   
248                             Ioffe Institute    research organisation   
42           University of California, Berkeley               university   
74        Massachusetts Institute of Technology  institute of technology   
54                          Columbia University       private university   
294  Moscow Institute of Physics and Technology  institute of technology   
37                           Harvard University       private university   

    membersNumber  
106            63  
248            37  
42            122  
74            132  
54             71  
294            25  
37            125  

Number of communitites: 18
Number of nodes per community: [273, 142, 107, 66, 40, 35, 35, 21, 20, 14, 12, 9, 8, 6, 5, 4, 4, 2]

Communities: 


Community 0
Betweenness|     | label                                 | mainType                |   membersNumber |
|----:|:--------------------------------------|:------------------------|----------------:|
| 106 | Leiden University                     | university              |              63 |
|  42 | University of California, Berkeley    | university              |             122 |
|  74 | Massachusetts Institute of Technology | institute of technology |             132 |
|  54 | Columbia University                   | private university      |              71 |
|  37 | Harvard University                    | private university      |             125 |
-----
Eigenvector|    | label                                 | mainType                |   membersNumber |
|---:|:--------------------------------------|:------------------------|----------------:|
| 37 | Harvard University                    | private university      |             125 |
| 77 | Princeton University                  | private university      |              85 |
| 36 | University of Chicago                 | private university      |             109 |
| 74 | Massachusetts Institute of Technology | institute of technology |             132 |
| 54 | Columbia University                   | private university      |              71 |

Community 1
Betweenness|     | label                                            | mainType                |   membersNumber |
|----:|:-------------------------------------------------|:------------------------|----------------:|
| 248 | Ioffe Institute                                  | research organisation   |              37 |
| 294 | Moscow Institute of Physics and Technology       | institute of technology |              25 |
| 297 | Moscow State University                          | public university       |             131 |
| 250 | Kharkiv Institute of Physics and Technology      | research organisation   |              26 |
| 404 | P.L. Kapitza Institute for Physical Problems RAS | academy of sciences     |              12 |
-----
Eigenvector|     | label                                            | mainType                |   membersNumber |
|----:|:-------------------------------------------------|:------------------------|----------------:|
| 417 | University of Groningen                          | university              |              26 |
| 248 | Ioffe Institute                                  | research organisation   |              37 |
| 294 | Moscow Institute of Physics and Technology       | institute of technology |              25 |
| 404 | P.L. Kapitza Institute for Physical Problems RAS | academy of sciences     |              12 |
| 297 | Moscow State University                          | public university       |             131 |

Community 2
Betweenness|     | label                    | mainType          |   membersNumber |
|----:|:-------------------------|:------------------|----------------:|
|  22 | University of Cambridge  | university        |             114 |
| 280 | University of Birmingham | university        |              24 |
| 195 | University of Bristol    | public university |              35 |
| 348 | University of Manchester | university        |              24 |
| 241 | Imperial College London  | university        |              38 |
-----
Eigenvector|     | label                    | mainType          |   membersNumber |
|----:|:-------------------------|:------------------|----------------:|
|  22 | University of Cambridge  | university        |             114 |
| 195 | University of Bristol    | public university |              35 |
| 280 | University of Birmingham | university        |              24 |
| 240 | University of Edinburgh  | public university |              32 |
| 178 | King's College London    | university        |              22 |

Community 3
Betweenness|     | label                         | mainType                |   membersNumber |
|----:|:------------------------------|:------------------------|----------------:|
| 342 | University of Göttingen       | public university       |              77 |
| 511 | University of Vienna          | university              |              57 |
| 515 | Technische Universität Berlin | institute of technology |              50 |
| 457 | TU Dresden                    | public university       |              26 |
|  96 | Humboldt University of Berlin | university              |              45 |
-----
Eigenvector|     | label                             | mainType                |   membersNumber |
|----:|:----------------------------------|:------------------------|----------------:|
| 342 | University of Göttingen           | public university       |              77 |
| 510 | University of Hamburg             | public university       |              17 |
| 515 | Technische Universität Berlin     | institute of technology |              50 |
| 362 | Technical University of Darmstadt | public university       |              13 |
| 511 | University of Vienna              | university              |              57 |

Community 4
Betweenness|     | label               | mainType   |   membersNumber |
|----:|:--------------------|:-----------|----------------:|
|  28 | University of Tokyo | university |              83 |
|  27 | Osaka University    | university |              25 |
|  89 | Nagoya University   | university |               8 |
|  26 | Tohoku University   | university |               7 |
| 270 | Kyoto University    | university |              29 |
-----
Eigenvector|     | label                         | mainType              |   membersNumber |
|----:|:------------------------------|:----------------------|----------------:|
|  28 | University of Tokyo           | university            |              83 |
| 270 | Kyoto University              | university            |              29 |
|  27 | Osaka University              | university            |              25 |
| 227 | Tokyo University of Education | university            |               3 |
| 228 | RIKEN                         | research organisation |               2 |



## Values for 1921-1940

Number of relationships for this period 3787

Number of nodes: 1244
Number of edges: 3787

Just one big component with 1109 nodes

Number of nodes for first component: 1109
Number of edges for first component: 3662

[('university', 406), ('research organisation', 197), ('public university', 195), ('company', 78), ('private university', 48), ('academy of sciences', 42), ('astronomical observatory', 30), ('institute of technology', 30), ('governmenmt agency', 29), ('research facility', 29), ('scientific organisation', 15), ('publisher_edition', 7), ('learned society', 3)]

Spearman's rank correlation of eidenvector and betweenness: 0.5692602682817818

Eigenvector
                                     label                 mainType  \
44                      Harvard University       private university   
18   Massachusetts Institute of Technology  institute of technology   
149     University of California, Berkeley               university   
79                     Columbia University       private university   
22                    Princeton University       private university   
91                   University of Chicago       private university   
227           Institute for Advanced Study    research organisation   

    membersNumber  
44            254  
18            232  
149           205  
79            144  
22            134  
91            147  
227            27  
-----
Betweenness                                          label                 mainType  \
108     University of Illinois Urbana–Champaign               university   
18        Massachusetts Institute of Technology  institute of technology   
117                     Moscow State University        public university   
44                           Harvard University       private university   
22                         Princeton University       private university   
91                        University of Chicago       private university   
118  Moscow Institute of Physics and Technology  institute of technology   

    membersNumber  
108            72  
18            232  
117           201  
44            254  
22            134  
91            147  
118            93  

Number of communitites: 15
Number of nodes per community: [320, 198, 110, 107, 102, 88, 42, 37, 37, 19, 18, 17, 5, 5, 4]

Communities: 


Community 0
Betweenness|     | label                                   | mainType                |   membersNumber |
|----:|:----------------------------------------|:------------------------|----------------:|
| 108 | University of Illinois Urbana–Champaign | university              |              72 |
|  18 | Massachusetts Institute of Technology   | institute of technology |             232 |
|  44 | Harvard University                      | private university      |             254 |
|  22 | Princeton University                    | private university      |             134 |
|  91 | University of Chicago                   | private university      |             147 |
-----
Eigenvector|     | label                                 | mainType                |   membersNumber |
|----:|:--------------------------------------|:------------------------|----------------:|
|  44 | Harvard University                    | private university      |             254 |
|  18 | Massachusetts Institute of Technology | institute of technology |             232 |
| 149 | University of California, Berkeley    | university              |             205 |
|  79 | Columbia University                   | private university      |             144 |
|  22 | Princeton University                  | private university      |             134 |

Community 1
Betweenness|     | label                                        | mainType                |   membersNumber |
|----:|:---------------------------------------------|:------------------------|----------------:|
| 117 | Moscow State University                      | public university       |             201 |
| 118 | Moscow Institute of Physics and Technology   | institute of technology |              93 |
|  14 | Joint Institute for Nuclear Research         | research organisation   |              44 |
| 573 | Lebedev Physical Institute                   | academy of sciences     |              57 |
| 158 | National Research Centre Kurchatov Institute | research organisation   |              39 |
-----
Eigenvector|     | label                                      | mainType                |   membersNumber |
|----:|:-------------------------------------------|:------------------------|----------------:|
| 119 | Loughborough University                    | public university       |               2 |
| 117 | Moscow State University                    | public university       |             201 |
|  14 | Joint Institute for Nuclear Research       | research organisation   |              44 |
| 118 | Moscow Institute of Physics and Technology | institute of technology |              93 |
| 125 | University of Illinois at Chicago          | public university       |               6 |

Community 2
Betweenness|     | label                                  | mainType                |   membersNumber |
|----:|:---------------------------------------|:------------------------|----------------:|
| 136 | University of Texas at Austin          | university              |              41 |
| 457 | University of Hamburg                  | public university       |              56 |
| 486 | Ludwig-Maximilian-University in Munich | public university       |              42 |
| 621 | Karlsruhe Institute of Technology      | institute of technology |              25 |
| 729 | Technical University of Munich         | institute of technology |              53 |
-----
Eigenvector|     | label                                  | mainType                |   membersNumber |
|----:|:---------------------------------------|:------------------------|----------------:|
| 136 | University of Texas at Austin          | university              |              41 |
| 486 | Ludwig-Maximilian-University in Munich | public university       |              42 |
| 457 | University of Hamburg                  | public university       |              56 |
| 654 | Max Planck Institute for Physics       | research organisation   |              12 |
| 621 | Karlsruhe Institute of Technology      | institute of technology |              25 |

Community 3
Betweenness|     | label                                        | mainType              |   membersNumber |
|----:|:---------------------------------------------|:----------------------|----------------:|
| 410 | International Centre for Theoretical Physics | research organisation |               6 |
| 315 | National Center for Scientific Research      | research organisation |              33 |
| 252 | Weizmann Institute of Science                | public university     |              27 |
| 306 | Pierre and Marie Curie University            | university            |              18 |
| 309 | University of Paris-Sud                      | university            |              23 |
-----
Eigenvector|     | label                                        | mainType              |   membersNumber |
|----:|:---------------------------------------------|:----------------------|----------------:|
| 410 | International Centre for Theoretical Physics | research organisation |               6 |
| 315 | National Center for Scientific Research      | research organisation |              33 |
| 279 | École Normale Supérieure                     | public university     |              64 |
|  37 | Sapienza University of Rome                  | public university     |              36 |
| 421 | University of Turin                          | university            |              14 |

Community 4
Betweenness|     | label                     | mainType          |   membersNumber |
|----:|:--------------------------|:------------------|----------------:|
|  47 | University of Cambridge   | university        |             152 |
| 128 | University of Oxford      | public university |              71 |
| 205 | King's College London     | university        |              33 |
| 327 | University College London | university        |              53 |
| 329 | Purdue University         | university        |              33 |
-----
Eigenvector|     | label                    | mainType          |   membersNumber |
|----:|:-------------------------|:------------------|----------------:|
|  47 | University of Cambridge  | university        |             152 |
| 128 | University of Oxford     | public university |              71 |
|  46 | University of Manchester | university        |              53 |
| 205 | King's College London    | university        |              33 |
| 304 | University of Bristol    | public university |              35 |



## Values for 1941-1960

Number of relationships for this period 4893

Number of nodes: 1553
Number of edges: 4893

Just one big component with 2 nodes

Number of nodes for first component: 2
Number of edges for first component: 1



## Values for 1961-1980

Number of relationships for this period 3365

Number of nodes: 1172
Number of edges: 3365

Just one big component with 995 nodes

Number of nodes for first component: 995
Number of edges for first component: 3227

[('university', 342), ('research organisation', 238), ('public university', 194), ('company', 33), ('private university', 32), ('research facility', 28), ('astronomical observatory', 28), ('scientific organisation', 26), ('governmenmt agency', 24), ('institute of technology', 23), ('academy of sciences', 20), ('learned society', 5), ('publisher_edition', 2)]

Spearman's rank correlation of eidenvector and betweenness: 0.6636731534301016

Eigenvector
                                           label                 mainType  \
12                            Harvard University       private university   
172           University of California, Berkeley               university   
307        Smithsonian Astrophysical Observatory    research organisation   
134                         Princeton University       private university   
305  Harvard–Smithsonian Center for Astrophysics    research organisation   
17            California Institute of Technology               university   
306                      Smithsonian Institution  scientific organisation   

    membersNumber  
12            122  
172            93  
307            19  
134           120  
305            12  
17             92  
306             9  
-----
Betweenness                                     label                 mainType  \
102                                   CERN    research organisation   
17      California Institute of Technology               university   
172     University of California, Berkeley               university   
12                      Harvard University       private university   
103  Massachusetts Institute of Technology  institute of technology   
64                    University of Oxford        public university   
1                               ETH Zurich  institute of technology   

    membersNumber  
102            47  
17             92  
172            93  
12            122  
103           111  
64             71  
1              72  

Number of communitites: 12
Number of nodes per community: [279, 152, 145, 102, 84, 79, 70, 34, 24, 10, 9, 7]

Communities: 


Community 0
Betweenness|     | label                                 | mainType                |   membersNumber |
|----:|:--------------------------------------|:------------------------|----------------:|
|  17 | California Institute of Technology    | university              |              92 |
| 172 | University of California, Berkeley    | university              |              93 |
|  12 | Harvard University                    | private university      |             122 |
| 103 | Massachusetts Institute of Technology | institute of technology |             111 |
|  64 | University of Oxford                  | public university       |              71 |
-----
Eigenvector|     | label                                       | mainType              |   membersNumber |
|----:|:--------------------------------------------|:----------------------|----------------:|
|  12 | Harvard University                          | private university    |             122 |
| 172 | University of California, Berkeley          | university            |              93 |
| 307 | Smithsonian Astrophysical Observatory       | research organisation |              19 |
| 134 | Princeton University                        | private university    |             120 |
| 305 | Harvard–Smithsonian Center for Astrophysics | research organisation |              12 |

Community 1
Betweenness|     | label                                  | mainType                |   membersNumber |
|----:|:---------------------------------------|:------------------------|----------------:|
|   1 | ETH Zurich                             | institute of technology |              72 |
| 159 | University of Stuttgart                | public university       |              30 |
|  45 | Ludwig-Maximilian-University in Munich | public university       |              59 |
| 463 | Technische Universität Berlin          | institute of technology |              55 |
|  37 | RWTH Aachen University                 | public university       |              31 |
-----
Eigenvector|     | label                                  | mainType                |   membersNumber |
|----:|:---------------------------------------|:------------------------|----------------:|
|   1 | ETH Zurich                             | institute of technology |              72 |
| 159 | University of Stuttgart                | public university       |              30 |
|  45 | Ludwig-Maximilian-University in Munich | public university       |              59 |
| 441 | Technical University of Munich         | institute of technology |              48 |
|  14 | Max Planck Institute of Quantum Optics | research organisation   |              13 |

Community 2
Betweenness|     | label                                             | mainType                |   membersNumber |
|----:|:--------------------------------------------------|:------------------------|----------------:|
| 102 | CERN                                              | research organisation   |              47 |
| 291 | University of Hamburg                             | public university       |              29 |
| 331 | National Center for Scientific Research           | research organisation   |              26 |
| 166 | Swiss Federal Institute of Technology in Lausanne | institute of technology |              36 |
| 205 | CEA Saclay                                        | governmenmt agency      |              13 |
-----
Eigenvector|     | label                 | mainType              |   membersNumber |
|----:|:----------------------|:----------------------|----------------:|
| 102 | CERN                  | research organisation |              47 |
| 167 | DESY                  | research organisation |              19 |
| 205 | CEA Saclay            | governmenmt agency    |              13 |
| 291 | University of Hamburg | public university     |              29 |
| 168 | Fermilab              | research organisation |              13 |

Community 3
Betweenness|     | label                              | mainType           |   membersNumber |
|----:|:-----------------------------------|:-------------------|----------------:|
| 144 | Leiden University                  | university         |              51 |
| 486 | University of Manchester           | university         |              24 |
| 197 | Radboud University Nijmegen        | university         |              23 |
| 256 | Australian National University     | public university  |              20 |
| 219 | Consiglio Nazionale delle Ricerche | governmenmt agency |              11 |
-----
Eigenvector|     | label                       | mainType   |   membersNumber |
|----:|:----------------------------|:-----------|----------------:|
| 144 | Leiden University           | university |              51 |
| 197 | Radboud University Nijmegen | university |              23 |
|   2 | University of Amsterdam     | university |              49 |
| 409 | Utrecht University          | university |              36 |
| 196 | University of Twente        | university |               6 |

Community 4
Betweenness|     | label                               | mainType              |   membersNumber |
|----:|:------------------------------------|:----------------------|----------------:|
|  56 | National Institute for Astrophysics | research organisation |              14 |
| 225 | Sapienza University of Rome         | public university     |              33 |
| 233 | University of Rochester             | university            |              17 |
| 730 | University of Sheffield             | university            |               9 |
| 262 | University of Southampton           | public university     |              15 |
-----
Eigenvector|     | label                               | mainType              |   membersNumber |
|----:|:------------------------------------|:----------------------|----------------:|
| 233 | University of Rochester             | university            |              17 |
| 302 | University of Pisa                  | public university     |              33 |
| 295 | INFN Sezione di Pisa                | research organisation |               7 |
| 749 | University of Alberta               | university            |               6 |
|  56 | National Institute for Astrophysics | research organisation |              14 |



## Values for 1981-2000

Number of relationships for this period 939

Number of nodes: 528
Number of edges: 939

Just one big component with 372 nodes

Number of nodes for first component: 372
Number of edges for first component: 821

[('university', 125), ('research organisation', 84), ('public university', 81), ('company', 18), ('research facility', 14), ('institute of technology', 14), ('scientific organisation', 10), ('private university', 10), ('astronomical observatory', 6), ('governmenmt agency', 6), ('academy of sciences', 3), ('publisher_edition', 1)]

Spearman's rank correlation of eidenvector and betweenness: 0.4292489904464427

Eigenvector
                                                 label  \
32                                                CERN   
31                                            Fermilab   
92                  University of California, Berkeley   
53               Massachusetts Institute of Technology   
169               SLAC National Accelerator Laboratory   
83   Swiss Federal Institute of Technology in Lausanne   
167                             University of Tübingen   

                    mainType membersNumber  
32     research organisation            20  
31     research organisation             7  
92                university            21  
53   institute of technology            32  
169    research organisation             2  
83   institute of technology            10  
167        public university             6  
-----
Betweenness                                     label                 mainType  \
32                                    CERN    research organisation   
68          Los Alamos National Laboratory        research facility   
118                     Harvard University       private university   
59                 University of Cambridge               university   
110                   Princeton University       private university   
92      University of California, Berkeley               university   
53   Massachusetts Institute of Technology  institute of technology   

    membersNumber  
32             20  
68             13  
118            36  
59             22  
110            19  
92             21  
53             32  

Number of communitites: 13
Number of nodes per community: [59, 55, 51, 46, 27, 26, 24, 23, 22, 15, 10, 7, 7]

Communities: 


Community 0
Betweenness|     | label                              | mainType                |   membersNumber |
|----:|:-----------------------------------|:------------------------|----------------:|
| 118 | Harvard University                 | private university      |              36 |
|  92 | University of California, Berkeley | university              |              21 |
| 121 | Stanford University                | private university      |              29 |
| 103 | ETH Zurich                         | institute of technology |              13 |
|  89 | Cornell University                 | private university      |               7 |
-----
Eigenvector|     | label                              | mainType           |   membersNumber |
|----:|:-----------------------------------|:-------------------|----------------:|
|  92 | University of California, Berkeley | university         |              21 |
| 121 | Stanford University                | private university |              29 |
| 118 | Harvard University                 | private university |              36 |
|  89 | Cornell University                 | private university |               7 |
|  66 | Northwestern University            | university         |               4 |

Community 1
Betweenness|    | label                 | mainType              |   membersNumber |
|---:|:----------------------|:----------------------|----------------:|
| 32 | CERN                  | research organisation |              20 |
| 84 | CEA Saclay            | governmenmt agency    |               5 |
| 27 | University of Geneva  | university            |               7 |
| 31 | Fermilab              | research organisation |               7 |
| 29 | Heidelberg University | public university     |              12 |
-----
Eigenvector|    | label                                             | mainType                |   membersNumber |
|---:|:--------------------------------------------------|:------------------------|----------------:|
| 32 | CERN                                              | research organisation   |              20 |
| 31 | Fermilab                                          | research organisation   |               7 |
| 83 | Swiss Federal Institute of Technology in Lausanne | institute of technology |              10 |
| 84 | CEA Saclay                                        | governmenmt agency      |               5 |
| 14 | University of Padua                               | university              |               8 |

Community 2
Betweenness|     | label                              | mainType          |   membersNumber |
|----:|:-----------------------------------|:------------------|----------------:|
|  59 | University of Cambridge            | university        |              22 |
|  56 | California Institute of Technology | university        |              24 |
|  58 | University of Washington           | public university |              18 |
| 279 | University College London          | university        |              13 |
| 126 | University of Warsaw               | university        |              23 |
-----
Eigenvector|    | label                                | mainType          |   membersNumber |
|---:|:-------------------------------------|:------------------|----------------:|
| 59 | University of Cambridge              | university        |              22 |
| 57 | Johns Hopkins University             | university        |               4 |
| 58 | University of Washington             | public university |              18 |
| 56 | California Institute of Technology   | university        |              24 |
| 54 | University of California, Santa Cruz | university        |               5 |

Community 3
Betweenness|     | label                                         | mainType              |   membersNumber |
|----:|:----------------------------------------------|:----------------------|----------------:|
|  68 | Los Alamos National Laboratory                | research facility     |              13 |
|  67 | Northeastern University                       | university            |               4 |
| 327 | Aalto University                              | public university     |               5 |
| 317 | University of Tartu                           | public university     |               8 |
| 261 | Max Planck Institute for the Science of Light | research organisation |               3 |
-----
Eigenvector|     | label                          | mainType              |   membersNumber |
|----:|:-------------------------------|:----------------------|----------------:|
|  68 | Los Alamos National Laboratory | research facility     |              13 |
| 158 | IBM                            | company               |               3 |
|  67 | Northeastern University        | university            |               4 |
|  65 | Dana–Farber Cancer Institute   | research organisation |               2 |
| 155 | University of Colorado         | university            |               3 |

Community 4
Betweenness|     | label                          | mainType          |   membersNumber |
|----:|:-------------------------------|:------------------|----------------:|
| 252 | University of Freiburg         | public university |               7 |
| 258 | University of Sheffield        | university        |               2 |
| 303 | Newcastle University           | university        |               2 |
| 253 | University of Würzburg         | public university |               8 |
| 264 | Katholieke Universiteit Leuven | university        |               5 |
-----
Eigenvector|     | label                                   | mainType              |   membersNumber |
|----:|:----------------------------------------|:----------------------|----------------:|
| 253 | University of Würzburg                  | public university     |               8 |
| 252 | University of Freiburg                  | public university     |               7 |
| 199 | Bell Labs                               | research organisation |               2 |
| 204 | Office of Science                       | governmenmt agency    |               1 |
| 281 | Ostfalia University of Applied Sciences | public university     |               1 |
