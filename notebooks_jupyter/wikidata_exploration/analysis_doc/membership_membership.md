# Report for relations: membership_membership

periods
1751-1800     740
1801-1850     876
1851-1900    1463
1901-1920     966
1921-1940    1387
1941-1960     995
1961-1980     267
1981-2000      26
dtype: int64



## Values for 1751-1800

Number of relationships for this period 740

Number of nodes: 97
Number of edges: 740

Just one big component with 94 nodes

Number of nodes for first component: 94
Number of edges for first component: 738

[('learned society', 49), ('academy of sciences', 29), ('scientific organisation', 13), ('company', 1), ('governmenmt agency', 1), ('publisher_edition', 1)]

Spearman's rank correlation of eidenvector and betweenness: 0.8644678241408034

Eigenvector
                                          label             mainType  \
2                                 Royal Society      learned society   
7            Royal Prussian Academy of Sciences  academy of sciences   
10        American Academy of Arts and Sciences      learned society   
4             Royal Swedish Academy of Sciences  academy of sciences   
11  Bavarian Academy of Sciences and Humanities  academy of sciences   
3                    French Academy of Sciences  academy of sciences   
5                  Academy of Sciences of Turin  academy of sciences   

   membersNumber  
2            129  
7             75  
10            61  
4             57  
11            76  
3             71  
5             83  
-----
Betweenness                                                label  \
5                        Academy of Sciences of Turin   
4                   Royal Swedish Academy of Sciences   
3                          French Academy of Sciences   
10              American Academy of Arts and Sciences   
2                                       Royal Society   
30  Royal Academy of Science, Letters and Fine Art...   
11        Bavarian Academy of Sciences and Humanities   

                   mainType membersNumber  
5       academy of sciences            83  
4       academy of sciences            57  
3       academy of sciences            71  
10          learned society            61  
2           learned society           129  
30  scientific organisation             3  
11      academy of sciences            76  

Number of communitites: 4
Number of nodes per community: [65, 13, 8, 8]



## Values for 1801-1850

Number of relationships for this period 876

Number of nodes: 135
Number of edges: 876

Just one big component with 121 nodes

Number of nodes for first component: 121
Number of edges for first component: 867

[('learned society', 57), ('academy of sciences', 31), ('scientific organisation', 28), ('research organisation', 2), ('astronomical observatory', 1), ('publisher_edition', 1), ('university', 1)]

Spearman's rank correlation of eidenvector and betweenness: 0.8125549656381857

Eigenvector
                                          label             mainType  \
2                                 Royal Society      learned society   
9            Royal Prussian Academy of Sciences  academy of sciences   
26        American Academy of Arts and Sciences      learned society   
4             Royal Swedish Academy of Sciences  academy of sciences   
5                  National Academy of Sciences  academy of sciences   
15                  Russian Academy of Sciences  academy of sciences   
27  Bavarian Academy of Sciences and Humanities  academy of sciences   

   membersNumber  
2            180  
9             94  
26           113  
4             88  
5             90  
15            70  
27            79  
-----
Betweenness                                    label             mainType membersNumber
3              French Academy of Sciences  academy of sciences            78
2                           Royal Society      learned society           180
45  German Academy of Sciences Leopoldina      learned society           131
24           Academy of Sciences of Turin  academy of sciences            85
5            National Academy of Sciences  academy of sciences            90
10                        Lincean Academy  academy of sciences            48
8          Société Philomathique de Paris      learned society            17

Number of communitites: 9
Number of nodes per community: [86, 16, 4, 3, 3, 3, 2, 2, 2]

Communities: 


Community 0
Betweenness|    | label                                 | mainType            |   membersNumber |
|---:|:--------------------------------------|:--------------------|----------------:|
|  3 | French Academy of Sciences            | academy of sciences |              78 |
|  2 | Royal Society                         | learned society     |             180 |
| 45 | German Academy of Sciences Leopoldina | learned society     |             131 |
| 24 | Academy of Sciences of Turin          | academy of sciences |              85 |
|  5 | National Academy of Sciences          | academy of sciences |              90 |
-----
Eigenvector|    | label                                 | mainType            |   membersNumber |
|---:|:--------------------------------------|:--------------------|----------------:|
|  2 | Royal Society                         | learned society     |             180 |
|  9 | Royal Prussian Academy of Sciences    | academy of sciences |              94 |
| 26 | American Academy of Arts and Sciences | learned society     |             113 |
|  4 | Royal Swedish Academy of Sciences     | academy of sciences |              88 |
|  5 | National Academy of Sciences          | academy of sciences |              90 |

Community 1
Betweenness|    | label                                                                 | mainType                |   membersNumber |
|---:|:----------------------------------------------------------------------|:------------------------|----------------:|
| 18 | Royal Astronomical Society                                            | learned society         |              12 |
| 74 | National Society of the Natural Sciences and Mathematics of Cherbourg | learned society         |               3 |
| 85 | Pontifical Academy of Sciences                                        | academy of sciences     |               3 |
| 79 | Q26898036                                                             | scientific organisation |               1 |
| 80 | Accademia dei Fisiocritici                                            | academy of sciences     |               1 |
-----
Eigenvector|    | label                                       | mainType                |   membersNumber |
|---:|:--------------------------------------------|:------------------------|----------------:|
| 18 | Royal Astronomical Society                  | learned society         |              12 |
| 76 | Accademia Pontaniana                        | academy of sciences     |               3 |
| 78 | Istituto Veneto di Scienze, Lettere ed Arti | scientific organisation |               2 |
| 84 | German Astronomical Society                 | learned society         |               2 |
| 85 | Pontifical Academy of Sciences              | academy of sciences     |               3 |

Community 2
Betweenness|     | label                                                  | mainType        |   membersNumber |
|----:|:-------------------------------------------------------|:----------------|----------------:|
|  99 | Société d'encouragement pour l'industrie nationale     | learned society |               2 |
|  95 | Société Française de Physique                          | learned society |               2 |
|  97 | Académie des Sciences, Arts et Belles-Lettres de Dijon | learned society |               1 |
| 114 | Société industrielle de Mulhouse                       | learned society |               1 |
-----
Eigenvector|     | label                                                  | mainType        |   membersNumber |
|----:|:-------------------------------------------------------|:----------------|----------------:|
|  99 | Société d'encouragement pour l'industrie nationale     | learned society |               2 |
|  95 | Société Française de Physique                          | learned society |               2 |
|  97 | Académie des Sciences, Arts et Belles-Lettres de Dijon | learned society |               1 |
| 114 | Société industrielle de Mulhouse                       | learned society |               1 |

Community 3
Betweenness|    | label                                   | mainType                |   membersNumber |
|---:|:----------------------------------------|:------------------------|----------------:|
| 21 | Finnish Society of Sciences and Letters | academy of sciences     |               4 |
| 19 | Fauna and Flora Society                 | scientific organisation |               1 |
| 20 | Finnish Literature Society              | learned society         |               1 |
-----
Eigenvector|    | label                                   | mainType                |   membersNumber |
|---:|:----------------------------------------|:------------------------|----------------:|
| 21 | Finnish Society of Sciences and Letters | academy of sciences     |               4 |
| 19 | Fauna and Flora Society                 | scientific organisation |               1 |
| 20 | Finnish Literature Society              | learned society         |               1 |

Community 4
Betweenness|    | label                                                             | mainType        |   membersNumber |
|---:|:------------------------------------------------------------------|:----------------|----------------:|
|  7 | Comité des Travaux Historiques et Scientifiques                   | learned society |               2 |
| 71 | Société française de médecine thermale de Paris                   | learned society |               1 |
| 72 | Académie des sciences, inscriptions et belles-lettres de Toulouse | learned society |               1 |
-----
Eigenvector|    | label                                                             | mainType        |   membersNumber |
|---:|:------------------------------------------------------------------|:----------------|----------------:|
|  7 | Comité des Travaux Historiques et Scientifiques                   | learned society |               2 |
| 71 | Société française de médecine thermale de Paris                   | learned society |               1 |
| 72 | Académie des sciences, inscriptions et belles-lettres de Toulouse | learned society |               1 |



## Values for 1851-1900

Number of relationships for this period 1463

Number of nodes: 212
Number of edges: 1463

Just one big component with 193 nodes

Number of nodes for first component: 193
Number of edges for first component: 1453

[('learned society', 68), ('academy of sciences', 59), ('scientific organisation', 49), ('governmenmt agency', 6), ('publisher_edition', 5), ('university', 3), ('company', 1), ('public university', 1), ('research organisation', 1)]

Spearman's rank correlation of eidenvector and betweenness: 0.7661809772275321

Eigenvector
                                    label             mainType membersNumber
6            National Academy of Sciences  academy of sciences           200
46  American Academy of Arts and Sciences      learned society           190
2                           Royal Society      learned society           232
16      Royal Swedish Academy of Sciences  academy of sciences           103
27            Russian Academy of Sciences  academy of sciences            88
4         Academy of Sciences of the USSR  academy of sciences           133
7   German Academy of Sciences Leopoldina      learned society           177
-----
Betweenness                                                 label  \
3                           French Academy of Sciences   
114                Deutsche Physikalische Gesellschaft   
2                                        Royal Society   
76   Royal Academy of Exact, Physical and Natural S...   
4                      Academy of Sciences of the USSR   
9          Bavarian Academy of Sciences and Humanities   
68                      American Philosophical Society   

                    mainType membersNumber  
3        academy of sciences            94  
114  scientific organisation            18  
2            learned society           232  
76       academy of sciences            16  
4        academy of sciences           133  
9        academy of sciences            62  
68           learned society            43  

Number of communitites: 6
Number of nodes per community: [121, 39, 27, 2, 2, 2]

Communities: 


Community 0
Betweenness|     | label                                       | mainType                |   membersNumber |
|----:|:--------------------------------------------|:------------------------|----------------:|
|   3 | French Academy of Sciences                  | academy of sciences     |              94 |
| 114 | Deutsche Physikalische Gesellschaft         | scientific organisation |              18 |
|   2 | Royal Society                               | learned society         |             232 |
|   4 | Academy of Sciences of the USSR             | academy of sciences     |             133 |
|   9 | Bavarian Academy of Sciences and Humanities | academy of sciences     |              62 |
-----
Eigenvector|    | label                                 | mainType            |   membersNumber |
|---:|:--------------------------------------|:--------------------|----------------:|
|  6 | National Academy of Sciences          | academy of sciences |             200 |
| 46 | American Academy of Arts and Sciences | learned society     |             190 |
|  2 | Royal Society                         | learned society     |             232 |
| 16 | Royal Swedish Academy of Sciences     | academy of sciences |             103 |
| 27 | Russian Academy of Sciences           | academy of sciences |              88 |

Community 1
Betweenness|    | label                          | mainType        |   membersNumber |
|---:|:-------------------------------|:----------------|----------------:|
| 17 | Société Française de Physique  | learned society |               9 |
| 65 | Academia pro Interlingua       | learned society |               5 |
|  8 | Polish Academy of Sciences     | learned society |              29 |
| 20 | Astronomical Society of France | learned society |              17 |
| 50 | Royal Astronomical Society     | learned society |              24 |
-----
Eigenvector|    | label                          | mainType        |   membersNumber |
|---:|:-------------------------------|:----------------|----------------:|
|  8 | Polish Academy of Sciences     | learned society |              29 |
| 11 | Bureau des Longitudes          | learned society |               8 |
|  1 | New York Academy of Sciences   | learned society |               3 |
| 50 | Royal Astronomical Society     | learned society |              24 |
| 20 | Astronomical Society of France | learned society |              17 |

Community 2
Betweenness|     | label                                                 | mainType            |   membersNumber |
|----:|:------------------------------------------------------|:--------------------|----------------:|
|  76 | Royal Academy of Exact, Physical and Natural Sciences | academy of sciences |              16 |
|  77 | Royal Academy of Sciences and Arts of Barcelona       | academy of sciences |              16 |
|  28 | Royal Meteorological Society                          | learned society     |               5 |
| 161 | Real Sociedad Española de Física y Química            | learned society     |               4 |
|  34 | Indian Academy of Sciences                            | academy of sciences |               2 |
-----
Eigenvector|     | label                                                 | mainType                |   membersNumber |
|----:|:------------------------------------------------------|:------------------------|----------------:|
| 108 | American Mathematical Society                         | learned society         |               3 |
|  76 | Royal Academy of Exact, Physical and Natural Sciences | academy of sciences     |              16 |
|  34 | Indian Academy of Sciences                            | academy of sciences     |               2 |
| 101 | Franklin Institute                                    | scientific organisation |               2 |
| 111 | Royal Academy of Fine Arts of Saint Isabel of Hungary | scientific organisation |               1 |

Community 3
Betweenness|     | label                                       | mainType        |   membersNumber |
|----:|:--------------------------------------------|:----------------|----------------:|
| 166 | All-Union Astronomical and Geodetic Society | learned society |               1 |
| 167 | Russian Society of Universe Explorers       | learned society |               2 |
-----
Eigenvector|     | label                                       | mainType        |   membersNumber |
|----:|:--------------------------------------------|:----------------|----------------:|
| 167 | Russian Society of Universe Explorers       | learned society |               2 |
| 166 | All-Union Astronomical and Geodetic Society | learned society |               1 |

Community 4
Betweenness|     | label                       | mainType                |   membersNumber |
|----:|:----------------------------|:------------------------|----------------:|
| 125 | German Astronomical Society | learned society         |               3 |
| 124 | Evangelical Academy         | scientific organisation |               1 |
-----
Eigenvector|     | label                       | mainType                |   membersNumber |
|----:|:----------------------------|:------------------------|----------------:|
| 125 | German Astronomical Society | learned society         |               3 |
| 124 | Evangelical Academy         | scientific organisation |               1 |



## Values for 1901-1920

Number of relationships for this period 966

Number of nodes: 178
Number of edges: 966

Just one big component with 168 nodes

Number of nodes for first component: 168
Number of edges for first component: 961

[('academy of sciences', 60), ('learned society', 53), ('scientific organisation', 41), ('research organisation', 5), ('publisher_edition', 4), ('governmenmt agency', 2), ('university', 2), ('company', 1)]

Spearman's rank correlation of eidenvector and betweenness: 0.7816710728555099

Eigenvector
                                    label             mainType membersNumber
15  American Academy of Arts and Sciences      learned society           247
11           National Academy of Sciences  academy of sciences           257
2                           Royal Society      learned society           168
17  German Academy of Sciences Leopoldina      learned society            90
6         Academy of Sciences of the USSR  academy of sciences           159
38              American Physical Society      learned society            58
20            Russian Academy of Sciences  academy of sciences            90
-----
Betweenness                                                label  \
4                          French Academy of Sciences   
24  American Association for the Advancement of Sc...   
57  Royal Academy of Exact, Physical and Natural S...   
38                          American Physical Society   
6                     Academy of Sciences of the USSR   
17              German Academy of Sciences Leopoldina   
19                   International Astronomical Union   

                   mainType membersNumber  
4       academy of sciences            49  
24  scientific organisation            33  
57      academy of sciences             9  
38          learned society            58  
6       academy of sciences           159  
17          learned society            90  
19  scientific organisation            32  

Number of communitites: 6
Number of nodes per community: [83, 60, 10, 6, 6, 3]

Communities: 


Community 0
Betweenness|    | label                                               | mainType                |   membersNumber |
|---:|:----------------------------------------------------|:------------------------|----------------:|
|  4 | French Academy of Sciences                          | academy of sciences     |              49 |
| 24 | American Association for the Advancement of Science | scientific organisation |              33 |
| 38 | American Physical Society                           | learned society         |              58 |
| 19 | International Astronomical Union                    | scientific organisation |              32 |
| 15 | American Academy of Arts and Sciences               | learned society         |             247 |
-----
Eigenvector|    | label                                 | mainType            |   membersNumber |
|---:|:--------------------------------------|:--------------------|----------------:|
| 15 | American Academy of Arts and Sciences | learned society     |             247 |
| 11 | National Academy of Sciences          | academy of sciences |             257 |
|  2 | Royal Society                         | learned society     |             168 |
| 38 | American Physical Society             | learned society     |              58 |
| 67 | American Philosophical Society        | learned society     |              38 |

Community 1
Betweenness|    | label                                          | mainType            |   membersNumber |
|---:|:-----------------------------------------------|:--------------------|----------------:|
|  6 | Academy of Sciences of the USSR                | academy of sciences |             159 |
| 17 | German Academy of Sciences Leopoldina          | learned society     |              90 |
| 10 | Hungarian Academy of Sciences                  | academy of sciences |              25 |
| 58 | Heidelberg Academy for Sciences and Humanities | academy of sciences |              25 |
| 18 | Polish Academy of Sciences                     | learned society     |              31 |
-----
Eigenvector|    | label                                 | mainType            |   membersNumber |
|---:|:--------------------------------------|:--------------------|----------------:|
| 17 | German Academy of Sciences Leopoldina | learned society     |              90 |
|  6 | Academy of Sciences of the USSR       | academy of sciences |             159 |
| 20 | Russian Academy of Sciences           | academy of sciences |              90 |
| 10 | Hungarian Academy of Sciences         | academy of sciences |              25 |
| 18 | Polish Academy of Sciences            | learned society     |              31 |

Community 2
Betweenness|     | label                                                 | mainType                |   membersNumber |
|----:|:------------------------------------------------------|:------------------------|----------------:|
|  57 | Royal Academy of Exact, Physical and Natural Sciences | academy of sciences     |               9 |
| 141 | Royal Academy of Sciences and Arts of Barcelona       | academy of sciences     |               4 |
| 146 | Catholic Association of Propagandists                 | scientific organisation |               1 |
| 132 | Real Sociedad Española de Física y Química            | learned society         |               3 |
|  78 | Royal Spanish Academy                                 | scientific organisation |               1 |
-----
Eigenvector|     | label                                                 | mainType                |   membersNumber |
|----:|:------------------------------------------------------|:------------------------|----------------:|
|  57 | Royal Academy of Exact, Physical and Natural Sciences | academy of sciences     |               9 |
| 141 | Royal Academy of Sciences and Arts of Barcelona       | academy of sciences     |               4 |
| 132 | Real Sociedad Española de Física y Química            | learned society         |               3 |
| 146 | Catholic Association of Propagandists                 | scientific organisation |               1 |
|  78 | Royal Spanish Academy                                 | scientific organisation |               1 |

Community 3
Betweenness|     | label                                          | mainType                |   membersNumber |
|----:|:-----------------------------------------------|:------------------------|----------------:|
|  25 | American Geophysical Union                     | scientific organisation |               4 |
|  22 | Royal Meteorological Society                   | learned society         |               1 |
|  23 | Journal of the Meteorological Society of Japan | publisher_edition       |               1 |
|  26 | American Meteorological Society                | learned society         |               1 |
| 154 | Society of Women Engineers                     | scientific organisation |               1 |
-----
Eigenvector|     | label                                          | mainType                |   membersNumber |
|----:|:-----------------------------------------------|:------------------------|----------------:|
|  25 | American Geophysical Union                     | scientific organisation |               4 |
| 158 | Association of Lunar and Planetary Observers   | scientific organisation |               1 |
|  22 | Royal Meteorological Society                   | learned society         |               1 |
|  23 | Journal of the Meteorological Society of Japan | publisher_edition       |               1 |
|  26 | American Meteorological Society                | learned society         |               1 |

Community 4
Betweenness|     | label                                                       | mainType                |   membersNumber |
|----:|:------------------------------------------------------------|:------------------------|----------------:|
|   3 | Norwegian Academy of Science and Letters                    | academy of sciences     |              10 |
|  81 | International Society on General Relativity and Gravitation | learned society         |               3 |
| 129 | Israel Academy of Sciences and Humanities                   | academy of sciences     |               5 |
|  82 | Royal Physiographic Society in Lund                         | scientific organisation |               4 |
|  79 | Royal Norwegian Society of Sciences and Letters             | academy of sciences     |               5 |
-----
Eigenvector|     | label                                                       | mainType                |   membersNumber |
|----:|:------------------------------------------------------------|:------------------------|----------------:|
|   3 | Norwegian Academy of Science and Letters                    | academy of sciences     |              10 |
| 129 | Israel Academy of Sciences and Humanities                   | academy of sciences     |               5 |
|  82 | Royal Physiographic Society in Lund                         | scientific organisation |               4 |
|  79 | Royal Norwegian Society of Sciences and Letters             | academy of sciences     |               5 |
|  81 | International Society on General Relativity and Gravitation | learned society         |               3 |



## Values for 1921-1940

Number of relationships for this period 1387

Number of nodes: 231
Number of edges: 1387

Just one big component with 215 nodes

Number of nodes for first component: 215
Number of edges for first component: 1379

[('academy of sciences', 73), ('learned society', 67), ('scientific organisation', 46), ('research organisation', 11), ('governmenmt agency', 8), ('university', 4), ('publisher_edition', 4), ('company', 1), ('research facility', 1)]

Spearman's rank correlation of eidenvector and betweenness: 0.8222628746844504

Eigenvector
                                    label               mainType membersNumber
40  American Academy of Arts and Sciences        learned society           376
70           National Academy of Sciences    academy of sciences           387
68                          Royal Society        learned society           219
19            Russian Academy of Sciences    academy of sciences           201
84              American Physical Society        learned society           134
10                      Academia Europaea  research organisation           178
7         Academy of Sciences of the USSR    academy of sciences           147
-----
Betweenness                                                 label  \
33                    International Astronomical Union   
10                                   Academia Europaea   
84                           American Physical Society   
104                    National Academy of Engineering   
39   American Association for the Advancement of Sc...   
40               American Academy of Arts and Sciences   
4                           French Academy of Sciences   

                    mainType membersNumber  
33   scientific organisation           238  
10     research organisation           178  
84           learned society           134  
104      academy of sciences           112  
39   scientific organisation            51  
40           learned society           376  
4        academy of sciences            75  

Number of communitites: 6
Number of nodes per community: [110, 80, 11, 6, 5, 3]

Communities: 


Community 0
Betweenness|     | label                                               | mainType                |   membersNumber |
|----:|:----------------------------------------------------|:------------------------|----------------:|
|  33 | International Astronomical Union                    | scientific organisation |             238 |
|  84 | American Physical Society                           | learned society         |             134 |
| 104 | National Academy of Engineering                     | academy of sciences     |             112 |
|  39 | American Association for the Advancement of Science | scientific organisation |              51 |
|  40 | American Academy of Arts and Sciences               | learned society         |             376 |
-----
Eigenvector|    | label                                 | mainType            |   membersNumber |
|---:|:--------------------------------------|:--------------------|----------------:|
| 40 | American Academy of Arts and Sciences | learned society     |             376 |
| 70 | National Academy of Sciences          | academy of sciences |             387 |
| 68 | Royal Society                         | learned society     |             219 |
| 84 | American Physical Society             | learned society     |             134 |
|  4 | French Academy of Sciences            | academy of sciences |              75 |

Community 1
Betweenness|    | label                                         | mainType                |   membersNumber |
|---:|:----------------------------------------------|:------------------------|----------------:|
| 10 | Academia Europaea                             | research organisation   |             178 |
|  7 | Academy of Sciences of the USSR               | academy of sciences     |             147 |
| 11 | Royal Swedish Academy of Engineering Sciences | scientific organisation |              24 |
| 18 | Polish Academy of Sciences                    | learned society         |              71 |
| 19 | Russian Academy of Sciences                   | academy of sciences     |             201 |
-----
Eigenvector|    | label                                 | mainType              |   membersNumber |
|---:|:--------------------------------------|:----------------------|----------------:|
| 19 | Russian Academy of Sciences           | academy of sciences   |             201 |
| 10 | Academia Europaea                     | research organisation |             178 |
|  7 | Academy of Sciences of the USSR       | academy of sciences   |             147 |
| 16 | German Academy of Sciences Leopoldina | learned society       |              81 |
|  8 | Hungarian Academy of Sciences         | academy of sciences   |              44 |

Community 2
Betweenness|     | label                                  | mainType                |   membersNumber |
|----:|:---------------------------------------|:------------------------|----------------:|
| 139 | International Academy of Astronautics  | governmenmt agency      |               5 |
|  30 | American Geophysical Union             | scientific organisation |               6 |
| 133 | Geological Society of America          | learned society         |               1 |
| 208 | California Academy of Sciences         | learned society         |               1 |
| 138 | International Astronautical Federation | governmenmt agency      |               1 |
-----
Eigenvector|     | label                                  | mainType                |   membersNumber |
|----:|:---------------------------------------|:------------------------|----------------:|
| 139 | International Academy of Astronautics  | governmenmt agency      |               5 |
|  30 | American Geophysical Union             | scientific organisation |               6 |
| 138 | International Astronautical Federation | governmenmt agency      |               1 |
|  24 | Royal Meteorological Society           | learned society         |               1 |
|  25 | Deutsche Meteorologische Gesellschaft  | learned society         |               1 |

Community 3
Betweenness|     | label                                   | mainType              |   membersNumber |
|----:|:----------------------------------------|:----------------------|----------------:|
| 108 | Indian Academy of Sciences              | academy of sciences   |              25 |
|   5 | Indian National Science Academy         | publisher_edition     |              44 |
| 167 | The National Academy of Sciences, India | academy of sciences   |              15 |
| 168 | Atomic Energy Commission of India       | governmenmt agency    |               3 |
| 169 | National Institute of Advanced Studies  | research organisation |               1 |
-----
Eigenvector|     | label                                   | mainType              |   membersNumber |
|----:|:----------------------------------------|:----------------------|----------------:|
|   5 | Indian National Science Academy         | publisher_edition     |              44 |
| 108 | Indian Academy of Sciences              | academy of sciences   |              25 |
| 167 | The National Academy of Sciences, India | academy of sciences   |              15 |
| 168 | Atomic Energy Commission of India       | governmenmt agency    |               3 |
| 169 | National Institute of Advanced Studies  | research organisation |               1 |

Community 4
Betweenness|     | label                                         | mainType                |   membersNumber |
|----:|:----------------------------------------------|:------------------------|----------------:|
|  92 | Institute of Physics                          | learned society         |               4 |
|  88 | Swansea University                            | university              |               6 |
|  89 | King's College London                         | university              |              33 |
|  93 | Science Museum                                | scientific organisation |               1 |
| 202 | Manchester Literary and Philosophical Society | learned society         |               1 |
-----
Eigenvector|     | label                                         | mainType                |   membersNumber |
|----:|:----------------------------------------------|:------------------------|----------------:|
|  92 | Institute of Physics                          | learned society         |               4 |
|  88 | Swansea University                            | university              |               6 |
|  89 | King's College London                         | university              |              33 |
|  93 | Science Museum                                | scientific organisation |               1 |
| 202 | Manchester Literary and Philosophical Society | learned society         |               1 |



## Values for 1941-1960

Number of relationships for this period 995

Number of nodes: 220
Number of edges: 995

Just one big component with 200 nodes

Number of nodes for first component: 200
Number of edges for first component: 970

[('academy of sciences', 63), ('learned society', 55), ('scientific organisation', 51), ('research organisation', 16), ('publisher_edition', 7), ('governmenmt agency', 3), ('astronomical observatory', 2), ('company', 1), ('research facility', 1), ('university', 1)]

Spearman's rank correlation of eidenvector and betweenness: 0.7729556278668727

Eigenvector
                                                label  \
23                       National Academy of Sciences   
5               American Academy of Arts and Sciences   
16                   International Astronomical Union   
6                           American Physical Society   
57                                      Royal Society   
26                                  Academia Europaea   
4   American Association for the Advancement of Sc...   

                   mainType membersNumber  
23      academy of sciences           287  
5           learned society           272  
16  scientific organisation           621  
6           learned society           150  
57          learned society           186  
26    research organisation           212  
4   scientific organisation            50  
-----
Betweenness                                                 label  \
16                    International Astronomical Union   
26                                   Academia Europaea   
5                American Academy of Arts and Sciences   
6                            American Physical Society   
4    American Association for the Advancement of Sc...   
23                        National Academy of Sciences   
160                          European Physical Society   

                    mainType membersNumber  
16   scientific organisation           621  
26     research organisation           212  
5            learned society           272  
6            learned society           150  
4    scientific organisation            50  
23       academy of sciences           287  
160  scientific organisation             6  

Number of communitites: 6
Number of nodes per community: [67, 66, 52, 10, 3, 2]

Communities: 


Community 0
Betweenness|    | label                                       | mainType              |   membersNumber |
|---:|:--------------------------------------------|:----------------------|----------------:|
| 26 | Academia Europaea                           | research organisation |             212 |
| 25 | Austrian Academy of Sciences                | academy of sciences   |              30 |
|  1 | Russian Academy of Sciences                 | academy of sciences   |              69 |
| 80 | Bavarian Academy of Sciences and Humanities | academy of sciences   |              12 |
| 42 | German Academy of Sciences Leopoldina       | learned society       |              85 |
-----
Eigenvector|    | label                                 | mainType              |   membersNumber |
|---:|:--------------------------------------|:----------------------|----------------:|
| 26 | Academia Europaea                     | research organisation |             212 |
| 42 | German Academy of Sciences Leopoldina | learned society       |              85 |
| 14 | French Academy of Sciences            | academy of sciences   |              64 |
|  1 | Russian Academy of Sciences           | academy of sciences   |              69 |
| 58 | Royal Swedish Academy of Sciences     | academy of sciences   |              58 |

Community 1
Betweenness|     | label                            | mainType                |   membersNumber |
|----:|:---------------------------------|:------------------------|----------------:|
|  16 | International Astronomical Union | scientific organisation |             621 |
| 160 | European Physical Society        | scientific organisation |               6 |
|  17 | New York Academy of Sciences     | learned society         |              11 |
|  39 | American Geophysical Union       | scientific organisation |              11 |
|  29 | American Astronomical Society    | scientific organisation |              30 |
-----
Eigenvector|    | label                            | mainType                |   membersNumber |
|---:|:---------------------------------|:------------------------|----------------:|
| 16 | International Astronomical Union | scientific organisation |             621 |
| 29 | American Astronomical Society    | scientific organisation |              30 |
| 34 | Royal Astronomical Society       | learned society         |              10 |
| 39 | American Geophysical Union       | scientific organisation |              11 |
| 17 | New York Academy of Sciences     | learned society         |              11 |

Community 2
Betweenness|    | label                                               | mainType                |   membersNumber |
|---:|:----------------------------------------------------|:------------------------|----------------:|
|  5 | American Academy of Arts and Sciences               | learned society         |             272 |
|  6 | American Physical Society                           | learned society         |             150 |
|  4 | American Association for the Advancement of Science | scientific organisation |              50 |
| 23 | National Academy of Sciences                        | academy of sciences     |             287 |
| 57 | Royal Society                                       | learned society         |             186 |
-----
Eigenvector|    | label                                               | mainType                |   membersNumber |
|---:|:----------------------------------------------------|:------------------------|----------------:|
| 23 | National Academy of Sciences                        | academy of sciences     |             287 |
|  5 | American Academy of Arts and Sciences               | learned society         |             272 |
|  6 | American Physical Society                           | learned society         |             150 |
| 57 | Royal Society                                       | learned society         |             186 |
|  4 | American Association for the Advancement of Science | scientific organisation |              50 |

Community 3
Betweenness|     | label                                                 | mainType            |   membersNumber |
|----:|:------------------------------------------------------|:--------------------|----------------:|
|   9 | Royal Academy of Exact, Physical and Natural Sciences | academy of sciences |              11 |
| 167 | Real Academia de Doctores de España                   | learned society     |               4 |
| 169 | European Academy of Sciences                          | learned society     |               3 |
| 193 | Royal Academy of Sciences and Arts of Barcelona       | academy of sciences |               3 |
|   8 | Jakiunde                                              | learned society     |               3 |
-----
Eigenvector|     | label                                                 | mainType              |   membersNumber |
|----:|:------------------------------------------------------|:----------------------|----------------:|
|   9 | Royal Academy of Exact, Physical and Natural Sciences | academy of sciences   |              11 |
| 169 | European Academy of Sciences                          | learned society       |               3 |
| 167 | Real Academia de Doctores de España                   | learned society       |               4 |
|   8 | Jakiunde                                              | learned society       |               3 |
|   7 | Spanish National Research Council                     | research organisation |              11 |

Community 4
Betweenness|     | label                                   | mainType            |   membersNumber |
|----:|:----------------------------------------|:--------------------|----------------:|
| 126 | Indian Academy of Sciences              | academy of sciences |              17 |
|  87 | Indian National Science Academy         | publisher_edition   |              20 |
| 148 | The National Academy of Sciences, India | academy of sciences |              13 |
-----
Eigenvector|     | label                                   | mainType            |   membersNumber |
|----:|:----------------------------------------|:--------------------|----------------:|
|  87 | Indian National Science Academy         | publisher_edition   |              20 |
| 126 | Indian Academy of Sciences              | academy of sciences |              17 |
| 148 | The National Academy of Sciences, India | academy of sciences |              13 |



## Values for 1961-1980

Number of relationships for this period 267

Number of nodes: 111
Number of edges: 267

Just one big component with 103 nodes

Number of nodes for first component: 103
Number of edges for first component: 263

[('academy of sciences', 37), ('scientific organisation', 25), ('learned society', 22), ('research organisation', 12), ('governmenmt agency', 2), ('university', 2), ('company', 1), ('astronomical observatory', 1), ('publisher_edition', 1)]

Spearman's rank correlation of eidenvector and betweenness: 0.6357459003250965

Eigenvector
                                    label                 mainType  \
5            National Academy of Sciences      academy of sciences   
9   American Academy of Arts and Sciences          learned society   
23       International Astronomical Union  scientific organisation   
16                      Academia Europaea    research organisation   
18  German Academy of Sciences Leopoldina          learned society   
6               American Physical Society          learned society   
3                           Royal Society          learned society   

   membersNumber  
5             63  
9             55  
23           442  
16            54  
18            32  
6             46  
3             32  
-----
Betweenness                                             label                 mainType  \
23                International Astronomical Union  scientific organisation   
6                        American Physical Society          learned society   
5                     National Academy of Sciences      academy of sciences   
18           German Academy of Sciences Leopoldina          learned society   
67                   Canadian Astronomical Society          learned society   
46             Deutsche Physikalische Gesellschaft  scientific organisation   
77  Heidelberg Academy for Sciences and Humanities      academy of sciences   

   membersNumber  
23           442  
6             46  
5             63  
18            32  
67             2  
46             8  
77            11  

Number of communitites: 5
Number of nodes per community: [34, 22, 22, 20, 5]

Communities: 


Community 0
Betweenness|    | label                               | mainType                |   membersNumber |
|---:|:------------------------------------|:------------------------|----------------:|
| 23 | International Astronomical Union    | scientific organisation |             442 |
| 59 | Royal Swedish Academy of Sciences   | academy of sciences     |              13 |
| 44 | French Academy of Sciences          | academy of sciences     |              11 |
| 62 | Royal Physiographic Society in Lund | scientific organisation |               1 |
| 84 | German Astronomical Society         | learned society         |               3 |
-----
Eigenvector|    | label                            | mainType                |   membersNumber |
|---:|:---------------------------------|:------------------------|----------------:|
| 23 | International Astronomical Union | scientific organisation |             442 |
| 35 | Polish Astronomical Society      | scientific organisation |               9 |
| 51 | Institut Universitaire de France | research organisation   |              22 |
| 44 | French Academy of Sciences       | academy of sciences     |              11 |
| 53 | Die Junge Akademie               | academy of sciences     |               6 |

Community 1
Betweenness|    | label                                 | mainType            |   membersNumber |
|---:|:--------------------------------------|:--------------------|----------------:|
|  5 | National Academy of Sciences          | academy of sciences |              63 |
| 22 | Australian Academy of Science         | academy of sciences |               4 |
|  9 | American Academy of Arts and Sciences | learned society     |              55 |
|  3 | Royal Society                         | learned society     |              32 |
| 24 | Royal Society of Canada               | academy of sciences |               3 |
-----
Eigenvector|    | label                                 | mainType            |   membersNumber |
|---:|:--------------------------------------|:--------------------|----------------:|
|  5 | National Academy of Sciences          | academy of sciences |              63 |
|  9 | American Academy of Arts and Sciences | learned society     |              55 |
|  3 | Royal Society                         | learned society     |              32 |
| 37 | Chinese Academy of Sciences           | academy of sciences |              10 |
| 10 | Pontifical Academy of Sciences        | academy of sciences |               5 |

Community 2
Betweenness|    | label                                          | mainType              |   membersNumber |
|---:|:-----------------------------------------------|:----------------------|----------------:|
| 18 | German Academy of Sciences Leopoldina          | learned society       |              32 |
| 77 | Heidelberg Academy for Sciences and Humanities | academy of sciences   |              11 |
| 16 | Academia Europaea                              | research organisation |              54 |
| 80 | The World Academy of Sciences                  | academy of sciences   |               5 |
| 74 | Royal Netherlands Academy of Arts and Sciences | academy of sciences   |              17 |
-----
Eigenvector|    | label                                          | mainType              |   membersNumber |
|---:|:-----------------------------------------------|:----------------------|----------------:|
| 16 | Academia Europaea                              | research organisation |              54 |
| 18 | German Academy of Sciences Leopoldina          | learned society       |              32 |
| 27 | Austrian Academy of Sciences                   | academy of sciences   |              20 |
| 74 | Royal Netherlands Academy of Arts and Sciences | academy of sciences   |              17 |
| 26 | Hungarian Academy of Sciences                  | academy of sciences   |               9 |

Community 3
Betweenness|    | label                                               | mainType                |   membersNumber |
|---:|:----------------------------------------------------|:------------------------|----------------:|
|  6 | American Physical Society                           | learned society         |              46 |
| 46 | Deutsche Physikalische Gesellschaft                 | scientific organisation |               8 |
| 31 | American Association for the Advancement of Science | scientific organisation |               9 |
| 12 | Norwegian Academy of Science and Letters            | academy of sciences     |               3 |
| 96 | Saxon Academy of Sciences and Humanities            | academy of sciences     |               7 |
-----
Eigenvector|    | label                                               | mainType                |   membersNumber |
|---:|:----------------------------------------------------|:------------------------|----------------:|
|  6 | American Physical Society                           | learned society         |              46 |
| 31 | American Association for the Advancement of Science | scientific organisation |               9 |
| 56 | American Astronomical Society                       | scientific organisation |               5 |
| 46 | Deutsche Physikalische Gesellschaft                 | scientific organisation |               8 |
| 12 | Norwegian Academy of Science and Letters            | academy of sciences     |               3 |

Community 4
Betweenness|    | label                                         | mainType                |   membersNumber |
|---:|:----------------------------------------------|:------------------------|----------------:|
| 67 | Canadian Astronomical Society                 | learned society         |               2 |
| 63 | Centre for Research in Astrophysics of Québec | research organisation   |               1 |
| 64 | Kangaride                                     | company                 |               1 |
| 65 | Association francophone pour le savoir        | learned society         |               1 |
| 66 | Mouvement laïque québécois                    | scientific organisation |               1 |
-----
Eigenvector|    | label                                         | mainType                |   membersNumber |
|---:|:----------------------------------------------|:------------------------|----------------:|
| 67 | Canadian Astronomical Society                 | learned society         |               2 |
| 63 | Centre for Research in Astrophysics of Québec | research organisation   |               1 |
| 64 | Kangaride                                     | company                 |               1 |
| 65 | Association francophone pour le savoir        | learned society         |               1 |
| 66 | Mouvement laïque québécois                    | scientific organisation |               1 |



## Values for 1981-2000

Number of relationships for this period 26

Number of nodes: 17
Number of edges: 26

Beware: more than one big component !

Number of nodes for first component: 11
Number of edges for first component: 17
