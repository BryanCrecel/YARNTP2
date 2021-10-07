CRECEL JEAN CHARBEL DS4 20200160

TP3 : YARN & MapReduce 1  - Lab 2

# MapReduce JAVA

## 1.6 Send the JAR to the edge node
- 1.6.1 Microsoft Windows

```sh
	Status:	Connecting to hadoop-edge01.efrei.online...
	Status:	Using username "j.crecel". 
	Status:	Connected to hadoop-edge01.efrei.online
	Status:	Starting upload of C:\Users\j.crecel\workspace\hadoop-examples-mapreduce\target\hadoop-examples-mapreduce-1.0-SNAPSHOT-jar-with-dependencies.jar
	Status:	File transfer successful, transferred 58,977,112 bytes in 48 seconds
	Status:	Retrieving directory listing of "/home/j.crecel"...
	Status:	Listing directory /home/j.crecel
	Status:	Directory listing of "/home/j.crecel" successful
	Status:	Disconnected from server
```
- 1.6.3 Run the job

```sh
	Connecting to hadoop-edge01.efrei.online...
	Status:	Using username "j.crecel". 
	Status:	Connected to hadoop-edge01.efrei.online
	Status:	Renaming '/home/j.crecel/hadoop-examples-mapreduce-1.0-SNAPSHOT-jar-with-dependencies.jar' to '/home/j.crecel/hadoop-dependencies.jar'
	Status:	/home/j.crecel/hadoop-examples-mapreduce-1.0-SNAPSHOT-jar-with-dependencies.jar -> /home/j.crecel/hadoop-dependencies.jar
	Status:	File transfer successful, transferred 58,977,112 bytes in 32 seconds
```

 [j.crecel@hadoop-edge01 ~]$ ls
```sh
	Arthur       davini.txt               mapper.py   sudoku.dta  Vinci
	bonjour.txt  hadoop-dependencies.jar  reducer.py  Ulysses
```

 [j.crecel@hadoop-edge01 ~]$ hdfs dfs -copyFromLocal hadoop-dependencies.jar
 [j.crecel@hadoop-edge01 ~]$ hdfs dfs -ls
```sh
Found 11 items
	drwx------   - j.crecel j.crecel          0 2021-09-24 20:00 .Trash
	drwx------   - j.crecel j.crecel          0 2021-10-01 03:15 .staging
	-rw-r--r--   3 j.crecel j.crecel     656215 2021-09-29 19:34 Arthur
	-rw-r--r--   3 j.crecel j.crecel     541173 2021-09-29 19:35 Ulysses
	-rw-r--r--   3 j.crecel j.crecel     601122 2021-09-29 19:35 Vinci
	-rw--w--w-   3 j.crecel j.crecel         17 2021-09-24 09:36 bonjour.txt
	drwxr-xr-x   - j.crecel j.crecel          0 2021-09-29 18:07 data
	-rw-r--r--   3 j.crecel j.crecel     601122 2021-10-01 03:10 davini.txt
	drwxr-xr-x   - j.crecel j.crecel          0 2021-09-24 08:33 dossier
	-rw-r--r--   3 j.crecel j.crecel   58977112 2021-10-01 03:04 hadoop-dependencies.jar
	drwxr-xr-x   - j.crecel j.crecel          0 2021-10-01 03:15 wordcount
```

yarn jar   /usr/odp/current/hadoop-mapreduce-client/hadoop-mapreduce-examples.jar  \wordcount  /user/j.crecel/hadoop-dependencies.jar  /user/j.crecel/wordcount

```sh
	21/10/01 03:30:51 INFO impl.TimelineReaderClientImpl: Initialized TimelineReader URI=https://hadoop-master03.efrei.online:8199/ws/v2/timeline/, 	clusterId=yarn-cluster
	21/10/01 03:30:51 INFO client.AHSProxy: Connecting to Application History server at hadoop-master03.efrei.online/163.172.102.23:10200
	21/10/01 03:30:52 INFO hdfs.DFSClient: Created token for j.crecel: HDFS_DELEGATION_TOKEN owner=j.crecel@EFREI.ONLINE, renewer=yarn, realUser=, 	issueDate=1633051852085, maxDate=1633656652085, sequenceNumber=1562, masterKeyId=43 on ha-hdfs:efrei
	21/10/01 03:30:52 INFO security.TokenCache: Got dt for hdfs://efrei; Kind: HDFS_DELEGATION_TOKEN, Service: ha-hdfs:efrei, Ident: (token for 	j.crecel: HDFS_DELEGATION_TOKEN owner=j.crecel@EFREI.ONLINE, renewer=yarn, realUser=, issueDate=1633051852085, maxDate=1633656652085, 	sequenceNumber=1562, masterKeyId=43)
	org.apache.hadoop.mapred.FileAlreadyExistsException: Output directory hdfs://efrei/user/j.crecel/wordcount already exists
        at org.apache.hadoop.mapreduce.lib.output.FileOutputFormat.checkOutputSpecs(FileOutputFormat.java:164)
        at org.apache.hadoop.mapreduce.JobSubmitter.checkSpecs(JobSubmitter.java:277)
        at org.apache.hadoop.mapreduce.JobSubmitter.submitJobInternal(JobSubmitter.java:143)
        at org.apache.hadoop.mapreduce.Job$11.run(Job.java:1565)
        at org.apache.hadoop.mapreduce.Job$11.run(Job.java:1562)
        at java.security.AccessController.doPrivileged(Native Method)
        at javax.security.auth.Subject.doAs(Subject.java:422)
        at org.apache.hadoop.security.UserGroupInformation.doAs(UserGroupInformation.java:1762)
        at org.apache.hadoop.mapreduce.Job.submit(Job.java:1562)
        at org.apache.hadoop.mapreduce.Job.waitForCompletion(Job.java:1583)
        at org.apache.hadoop.examples.WordCount.main(WordCount.java:87)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
        at java.lang.reflect.Method.invoke(Method.java:498)
        at org.apache.hadoop.util.ProgramDriver$ProgramDescription.invoke(ProgramDriver.java:71)
        at org.apache.hadoop.util.ProgramDriver.run(ProgramDriver.java:144)
        at org.apache.hadoop.examples.ExampleDriver.main(ExampleDriver.java:74)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
        at java.lang.reflect.Method.invoke(Method.java:498)
        at org.apache.hadoop.util.RunJar.run(RunJar.java:323)
        at org.apache.hadoop.util.RunJar.main(RunJar.java:236)
```

	hdfs dfs -cat /user/j.crecel/wordcount/part-r-00000

```sh
seventh 4
several 31
severe  1
sex     2
shade   75
shade,  20
shade.  13
shade.] 1
shade;  2
shade?  2
shaded  33
shaded, 1
shaded; 1
shades  2
shades. 1
shading 2
shading.        1
shadow  338
shadow) 1
shadow).]       1
shadow).].      1
shadow);        1
shadow, 39
shadow-rays     1
shadow. 45
shadow:—One     1
shadow; 13
shadow] 1
shadowed        1
shadowing       1
shadowless      1
shadows 152
shadows,        17
shadows.        11
shadows;        4
shadows?        1
shadows—percussione     1
shadowy 2
shadow—so       1
shady   1
shall   30
shame   1
shape   14
shape,  1
shaped  2
shapes  1
shapes, 1
share   5
shared  1
sharp   2
sharpness       1
sharpness,      1
shattered;      1
she     5
shed    1
sheep.  1
sheet   9
sheet,  3
sheets  1
sheets, 1
sheets. 1
sheets—so       1
shewn   1
shield  1
shield, 1
shielding       1
shields,        1
shin    2
shine   1
shine,  1
shines  7
shines, 1
shining 1
ship    4
ships   1
ships,  2
shoot   11
shoot]  1
shooting        2
shoots  11
shoots. 1
shore   3
shore,  1
shore-sand      1
shores  1
shores. 1
short   19
short,  3
shortened;      1
shorter 3
shorter.        1
shortest        4
should  128
should, 1
shoulder        27
shoulder,       7
shoulder-blade  1
shoulderblades  2
shoulderblades. 2
shoulders       10
shoulders,      2
shoulders.      4
shoulders:      1
shouting        1
show    46
show,   5
showed  1
showing 5
shown   47
shown,  3
shown.] 1
shows   23
shows,  1
shows:  2
shows;  1
shrieking       1
shrink  4
shrink. 1
shrinking       1
shrinks 1
shrubs  1
shrubs, 1
shrugs  1
shut    7
shut,   1
shutting        2
shy     1
si      11
sia     1
sia.    1
sicuramente     1
side    166
side,   20
side.   18
side.]  3
side;   5
sides   31
sides,  2
sides.  2
sides;  3
sideways        1
side—and        1
side—if 1
sight   31
sight,  4
sight.  3
sight;  3
sight]  1
sight], 1
sights  1
sign    1
signify 8
signor  1
silent  1
silk,   1
sill,   1
silver  5
silver-point    4
similar 20
similarly,      1
similitude      1
simple  30
simpler 1
simpler,        1
simply  8
since   57
since,  12
sinew   1
sinew,  1
sinew;  1
sinews  5
sinews, 3
sinewy  2
singeing        1
single  37
singular        1
sink    1
sinking 1
sinks   1
sinuous 2
sites   2
sits—that       1
sitter  1
sitting 8
sitting,        2
situated        15
situated,       1
situation       2
six     12
sixteen 1
sixth   14
sixth.  1
sixths  1
sixty   1
size    86
size)   1
size,   19
size.   6
size;   3
size],  1
sizes   1
sketch  52
sketch, 8
sketch-book"    1
sketch. 2
sketch.]        5
sketched        4
sketched,       1
sketched.       1
sketches        45
sketches,       2
sketches.       1
sketches.]      1
sketching       3
skies,  1
skill,  1
skilled 2
skin    12
skin,   1
skin—four       1
skirt   1
sky     29
sky,    12
sky.    3
sky;    4
sky],   1
slaughter       2
slave   1
slender 9
slender.        1
slenderest      1
slew    1
slide,  1
sliding 1
slight  7
slight, 1
slightly        8
slip    1
slipped 1
slope   3
slope,  1
slopes  2
sloping 1
slow    3
slower  2
slowly  3
small   74
small,  6
small.  2
small;  1
smaller 73
smaller,        11
smaller.        4
smaller;        5
smallest        21
smallest.       4
smallness       1
smarting        1
smear   1
smell;  1
smells  2
sminuire,       1
smoke   32
smoke,  4
smoke.  3
smoke;  1
smooth  3
snakes  1
snow    2
snow,   1
snow;   1
so      224
so,     11
so.     1
so;     1
soaking 1
soap    2
soap.   1
soap;   1
socket  1
soft    4
softened,       1
softly  1
softly, 2
softness        1
software        2
software,       1
sogenannte      1
soil    1
sola    1
solanum 1
solar   12
soldiers        4
soldiers,       1
soldiers.       1
sole    9
solely  1
solicit 1
solicited       1
solid   14
solid.  1
solidity        1
solitary,       1
solitude        1
sollicito       1
solo    1
solo,   1
soltanto        1
solution        3
solution,       1
solve   1
some    133
someone 2
something       14
sometimes       11
somewhat        25
somigliantissimi        1
somita. 1
son     4
sono    5
sons    1
sons,   1
sont,   1
soon    5
sooner  7
soot    1
sophistry       1
sophistry,      3
sopra   1
sopradetto      1
sorest  1
sort    1
sorts   5
sotto   2
sotto.  1
sotto:  2
sought  4
soul    2
soul,   1
sound   9
sound,  2
sounded 1
sounds  2
source  12
source, 1
space   85
space,  3
space.  5
space;  1
spaces  21
spaces, 4
span's  1
spans   1
spans.  1
speak   3
speaker 2
speaker's       1
speaker,        2
speaker.        1
speakers,       1
speaking        5
speaking,       1
speaking.       1
speaks  5
speak—, 1
spear   1
spear,  1
spears  1
special 8
specialists.    1
specially       2
species 1
species.        1
specific        1
specimen        1
spectacles,     2
spectator       13
spectator's     1
spectator,      2
spectator.      5
spectator.]     1
spectator.].    1
spectator;      1
spectators      1
speculation     1
speculation;    1
speculations    1
speculations.   1
speech  1
speed.  1
spelling        1
spent   3
sphere  6
spherical       11
spherical,      1
spherical.      1
spine   2
spiracelo       1
spirit  2
spittle 1
splendid        2
splendour       1
split   1
spoil   2
spoilt  1
spoilt. 1
spoke   3
spoke;  1
spoken  9
sponge  1
spongy  2
spot    44
spot)   1
spot.   1
spot;   1
spots   5
spots,  3
spotted 1
spray   2
spread  10
spread, 1
spread; 1
spreading       3
spreading,      2
spreading.      1
spreads 2
spring  8
spring, 1
spring; 1
springs 6
sprinkle        1
sprinkled       1
spur    1
spurious.       1
squadrons       1
squandered      1
square  17
square, 2
square. 1
square.].       1
square; 1
squarely        1
squares 3
squares.        1
squaring        1
squash  1
stabbed 1
stable  1
staff   3
stage   4
stages  1
stagnant        1
stained 2
stains, 1
stairs  2
stanca  1
stand   31
stand,  1
stand.  1
standard        9
standing        22
standing,       2
stands  23
stands, 2
stands.]        1
star    4
star.   1
star;   1
stare   1
starlings].     1
stars   4
stars.  1
start   5
started 1
starting        6
starts  3
starts, 1
state   4
state.  1
state;  1
stated  5
stated.]        1
statement       6
statement.      4
statements      2
statements.—As  1
states  6
states. 3
stationary      3
stationary.     1
stato   1
statue  1
status  1
stay    2
stay,   1
steady  1
steady, 2
stecca  1
steeped 1
steht".]        1
stella: 1
stem    5
stem,   1
stem;   3
stems   3
stems;  1
stencil 1
stencil,        1
step    5
step;   1
stepped 1
steps   1
steps,  3
steps.  1
stereoscope     1
stern   3
stette."        1
stick   4
stick,  1
stick.].        1
sticking        1
sticks  2
sticks, 1
stiff   5
stiffness;      1
stigma  1
still   23
still,  6
still.  1
stilli."        1
stimulate       1
stippled        1
stomach 1
stone   2
stone,  1
stone.  1
stones  1
stones, 2
stones. 2
stood   3
stooping,       1
stooping;       1
stoops  1
stop    2
stop,   1
stopping        1
store   2
stored  1
storia, 1
storiche        1
storiche"       1
storm   2
storm-clouds,   1
stormy  1
storre  1
story   3
story,  1
story.  1
stout   1
stove   1
straggling,     1
straight        34
straight,       4
straight.       1
straightened    1
straightens     2
straightest     1
straightly      1
strain  2
strain; 1
strange 1
strangled       1
straw   1
streaked        1
stream  1
stream. 1
streaming       1
street  1
streets 2
streets,        1
stremi  1
strength        14
strength,       2
stretch 1
stretched       2
strewn  1
strict  1
strictly        1
strides 2
strike  8
strikes 5
striking        2
striking,       1
string, 1
string. 2
stringeva       1
strip   1
strip;  1
stripped        3
strive  1
strives 1
stroke  1
strokes 2
strong  15
strong, 2
strong. 2
stronger        14
strongest       5
strongest,      1
strongly        8
strongly.       1
struck  5
struck, 1
structure       5
struggle;       1
student 1
students        1
students,       1
studiarono      1
studied 3
studied,        2
studies 30
studies,        1
studies.        2
studies;        1
studies]        1
studio  2
studio, 1
studio-window.  1
studio. 2
study   32
study.  3
studying        4
stuff   1
stuffs  1
stupendous      1
style   4
style,  2
su      3
sua     1
subdivide       1
subdued 1
subject 25
subject,        4
subject-matter  1
subject.        4
subject;        1
subject_        1
subjected       2
subjects        7
subjects,       2
subjects.(5-8). 1
subjects;       1
sublimate,      2
sublimated      1
sublimita       1
submerge        1
submerged       1
subscribe       1
subsequent      5
subsequently    4
subsists        1
substance       4
substance.      1
substance:      1
substances.     1
substitute      1
substitute,     1
subtle  5
succeeding      1
success.        1
succession      3
succession,     1
successively    1
such    108
such,   1
suddenly        8
sudore, 1
sue     3
suffered        2
suffering       1
suffering;      1
suffice 2
sufficed        1
suffices        1
sufficient      7
sufficiently    3
suggest 3
suggested       3
suggestion      2
suggestion,     1
suggestion;     1
suggestions     6
suggestions.    1
suggestive      2
suggests        1
sugli   1
sui     1
suitable        2
sum     3
summed  1
summer  6
summer, 1
summer. 1
summer; 1
summing 1
summit  5
summits 1
summits,        1
summits;        1
summoned        1
sun     109
sun's   6
sun,    22
sun.    10
sun:    1
sun;    5
sunbeams        1
sundered.       1
sunk    1
sunlight        7
sunlight,       1
sunlight;       1
sunset, 1
sunshine        1
sunshine;       1
suo     2
superabundant   1
superficies     2
superfluity     1
superimposed    1
superior        4
superiority     2
supplant        1
supplement      3
supplement.     1
supplementary   1
supplied        2
support 6
support.        1
supported       3
supported,      1
supported.      1
supporting      2
supports        2
suppose 8
supposed        4
supposing       1
supposition     2
supposition,    1
supreme 4
sur     2
sure    2
surely  2
surer   1
surface 102
surface,        13
surface.        7
surface;        3
surfaces        7
surfaces,       1
surface—they    1
surprised       1
surprising      2
surround        8
surrounded      23
surrounding     30
surrounds       9
suspect 1
suspended       1
suspended.      1
swathing        1
sweep   1
swell   1
swelled 1
swelling        3
swelling,       1
swept   1
swift   3
swiftly 1
swine   1
swollen 3
sword   1
sword;  1
swords  1
symbolise       1
system, 1
systematic      1
systems 1
s—then, 1
t       22
t,      5
t.      3
t;      2
tabernacle,     1
table   2
tables, 2
tag     1
tagliato.       1
tail    2
take    52
taken   17
takes   15
taking  10
talent; 1
tali    1
talking,        1
tall    4
tall,   1
taller  1
tallest 1
tameness,       1
tan-coloured    1
tanta   3
tanto   3
tardi   1
target, 1
target. 1
tartar, 1
task    3
task.   1
taste   1
taste.  1
tatters 1
taught  1
tax     1
tax-deductible  1
tax-deductible, 1
taxes.  1
teaches 1
teaching        1
teachings       1
team.   1
tear    1
tearing 1
technical       2
tedious 1
tedium. 1
teeth   3
teeth,  1
teeth.  1
teeth;  1
tel     1
tell    11
tell.   3
tells   5
tempera 1
tempered        1
tempered,       1
tempest 4
tempest.        1
tempestuous     2
tempi   1
temple  1
temples 1
tempo   1
tempo." 1
ten     6
tenait  1
tend    6
tend;   1
tendency        1
tender  2
tending 1
tendon  2
tendon. 1
tendons 4
tendons,        2
tendons;        1
tends   3
tenor   1
tenour  1
tentativi       1
tenth   2
tents.  1
termed  1
terminal        1
terminate       5
terminated      1
terminates      4
terminating     2
termination     5
termination.    1
termine 1
terms   1
terra   1
terrestrial     2
terrible        2
terrified       3
terrify 1
terror  1
terza   1
terze   1
terzo   1
test    2
tested  1
tetragon        1
text    76
text,   17
text.   9
text.]  6
text;   1
texts   15
texts,  3
text—lines      1
than    356
than,   1
thanks  1
that    1110
that,   16
that.   1
that;   1
that]   3
the     9846
the)    1
the.    1
the:    1
the]    4
their   312
them    181
them".  1
them,   35
them.   37
them.]  2
them.]. 1
them._  1
them:   1
them;   11
them],  1
them].  1
theme—I 1
themselves      23
themselves,     2
themselves.     6
themselves;     2
them—appear     1
them—is 1
them—since      1
then    123
then,   9
thence  2
thence—being    1
then—beyond     1
theologian,     1
theoretical     6
theories        2
theory  17
theory, 2
theory. 2
theory; 1
there   130
there,  5
there.  5
there;  2
therefore       35
therefore,      4
therein 1
these   204
these,  9
these.  1
they    362
they,   2
they—who        1
thick   14
thick,  2
thick;  2
thicken,        1
thickened,      1
thickening      1
thicker 11
thicker,        2
thicker.        1
thickest        6
thickly 2
thickness       42
thickness,      1
thickness.      1
thickness]      1
thickness—in    1
thigh   7
thigh,  2
thigh.—The      1
thin    28
thin,   2
thin.   1
thing   55
thing,  2
thing.  3
thing;  2
things  32
things, 9
things. 1
things].        1
things—vouchsafe        1
thing—of        1
think   7
thinly  2
thinner 6
thinner.        2
thinnest        6
third   34
third,  2
third?  1
thirdly 2
thirds  2
third—the       1
thirteen        1
thirty  1
thirty-seventh  1
this    679
this,   15
this:   11
this:—The       1
this—and        1
thither 1
thorough        1
thoroughly      3
thoroughness    2
those   189
those,  1
thou    1
though  40
thought 3
thoughts        2
thousand        2
thread. 1
thread; 1
threads 1
threatening     1
threatens       1
three   50
three:  1
throat  8
throat, 1
throat. 1
throat; 1
throats 1
through 129
through.        1
throughout      11
throughout,     4
throw   12
throwing        3
thrown  16
thrown. 1
throws  8
thrust  5
thrusting,      1
thrusts 2
thumb   2
thumb,  1
thumb.  1
thunder 1
thunder-bolts   1
thunder-bolts.  1
thunderbolts    1
thunderbolts,   1
thunders        1
thus    50
thus,   3
thus.   1
thus:   3
thus:—[Footnote 1
thy     1
thè     1
tied    1
tightly 2
til     1
tilde   1
till    18
till,   1
time    51
time,   13
time.   6
time;   4
times   52
times,  2
times.  1
times;  1
timid   1
tinge   5
tinge,  2
tinged  7
tinges  4
tint    2
tint,   1
tinted  11
tints   3
tip     20
tip,    1
tip-toe 1
tips    4
tips;   1
tire    1
tired   1
tires   1
tirés   1
tissue  1
tissue.]        1
title   5
title-line      1
title-line;     1
title:  1
title]—I        1
titles  2
to      2106
to)     1
to,     4
to.     2
to:     2
to;     2
to]     1
toads   1
toe     8
toe,    2
toe.    2
toes    6
toes.   3
together        31
together,       9
together.       5
together:       1
told    2
told,   1
tolerable       1
tondo;  1
tone    14
tone,   5
tone.   1
tone;   1
tone]   1
toned   1
tongues 2
tongues.        1
too     34
too,    3
took    7
top     55
top,    1
top.    5
top;    1
topmost 3
tops    1
tops,   1
tops.   1
torch   1
torment 1
torment.        1
torn    3
torn,   1
torrents        1
torrents,       1
torso   13
torso,  1
torso.  1
tortoise.       1
tossed  6
total   4
totally 3
touch   5
touch;  1
touched 1
touches 4
touching        5
toujours        1
towards 123
tower   8
tower)  1
tower,  1
towers  2
town    1
town,   3
towns   3
towns,  1
trace   2
traced  3
tracing 3
track   1
tractato.—We    1
trademark       2
trademark.      1
tradition,      1
traditionally   1
tragedy 1
trailer 1
train   1
training        1
traitors,       1
tramontano      1
tramping        1
trampled        1
transcribe      2
transcription   1
transfer        2
transferred     2
transformed     1
translates      3
translation     5
translation,    1
translation.    1
transmission    4
transmit        12
transmits       4
transmitted     12
transmitting    3
transmuted      1
transparency    6
transparency,   1
transparency.   1
transparent     31
transparent,    4
transparent.    5
transparent;    2
transparent—that        1
transverse      3
tratto  1
travel  3
travels 2
tre     2
treading        1
treat   16
treat.  1
treated 7
treated.        1
treating        4
treatise        4
treatise,       1
treatise.]      1
treatment       9
treats  6
tree    57
tree,   8
tree.   8
tree;   2
tree]   1
trees   91
trees,  20
trees.  2
trees;  2
trees], 1
trees—onto      1
tremendous      2
triangle        9
triangle,       1
triangle.       1
triangle],      1
tribe.  1
tribolatione.   1
triboli 1
trick   1
tricks  1
trident,        1
tried   3
tries   2
trillion        1
trivial 1
troop   1
trop.   1
trophy  1
trouble 2
trouble.        1
troubled        1
trough  1
troughs,        1
trovano 1
trovati 1
troviamo        1
truce,  1
true    26
true,   7
true.   3
true:   1
true;   1
truly   1
truncated       1
trunk   4
trunk.] 1
trust   3
trustees        1
truth   4
truth,  2
truth.  1
truth;  1
truths  1
try     7
trying  2
tu      1
tua     1
tube    4
tumble  1
tuoi    1
turbid  1
turbulent       1
turmeric        2
turmoil 1
turn    30
turned  24
turned, 2
turning 3
turnips 1
turns   17
turns,  2
turpentine      2
tusks   1
tutta   2
tutte   3
tutti   1
tutto   3
twelfth 1
twelve  1
twentieth       1
twice   22
twice;  1
twin    2
twins   1
twins,  1
twist   2
twisted 3
twisting        1
twists, 1
two     184
two,    1
two-and-twenty  1
two:    1
two?    1
type    2
type]   1
types:  1
types;  1
u       1
u.      1
ucciso  1
uedere  1
ugly    1
ugly,   2
uiua    1
ultimi  1
um      1
umano". 1
un      14
un'arte 1
una     3
unable  4
unanswered      2
unanswered.]    1
unbearable      1
uncover 1
uncovered       2
und     3
undefined,      1
undefined;      1
under   70
underground     1
underline       1
underneath      1
underside       2
understand      12
understand,     2
understanding   5
understanding,  1
understood      14
understood.     4
undertakings    1
undiminished,   1
undiscovered    1
undistinguishable       2
undisturbed     1
undoubtedly     3
undulate        1
undulations     1
undulations.    1
une     2
unequal 7
unequal.        1
unfinished      2
unfinished;     1
unfortunate     1
unfortunately   4
unfounded       1
unfounded,      1
ungraceful.     1
uniform 12
uniformity      1
uniformly       2
unintelligible  2
unions  1
unique  1
unit    1
united  2
unites  1
universal       7
universale      1
universality    2
universality,   2
universe        1
universe,       1
unjustly        1
unknown 4
unknown.        1
unless  23
unless, 1
unlike  1
unmeaning       1
unnecessary     2
uno     2
unpublished,    1
unravelled      1
unrecognisable. 1
unrestricted    1
unsatisfactory.]        1
unsuccessful    1
unsuspecting    1
until   11
uomo    3
up      109
up,     8
up-side-down    1
up.     5
upbraiding      1
upon    54
upon.   1
upon—Bernardo   1
upper   48
upright 4
upright;        1
uprooted        1
uprooted,       1
upset,  1
upsets  1
upsetting.]     1
upside  12
upwards 4
upwards,        3
upwards.        1
upwards;        4
up—which        1
urged   1
urine   1
us      31
us,     5
us.     1
us;     3
use     27
use,    3
use:    1
used    17
used.   1
useful  10
useful, 2
useful. 2
usefulness      1
usefulness.     1
useless 2
useless.—       1
users.  1
uses    1
using   4
usual   2
usually 3
utile,  1
utility 3
utility.        2
utility—all     1
utmost  1
utmost. 1
utter   2
v       16
v,      2
v;      3
va      1
vacant, 1
vacuum  2
vague   2
vague.  1
vain    2
vain.   1
valley  3
valleys 3
valleys,        1
valorosi        1
valuable        5
value   6
value,  2
value.  2
value]; 1
value—all       1
van     1
vanish  1
vanishes        1
vanishing       4
vapour  4
vapour, 1
vapour. 2
vari    1
variable        1
variation       1
variation,      1
variations      6
variations,     1
variations;     1
varied  4
varies  11
varieties       3
variety 15
variety,        2
variety;        2
various 93
variously       1
varnish 9
varnish,        2
varnished,      1
varnishes       2
varnishes;      1
vary    12
vary,   2
vary.   2
varying 3
vase    1
vast    5
vault   1
vault.] 1
vaulted 1
vaunters        1
vede    3
vedere  1
vedere, 1
vediam  1
veduto  1
vegetali,       1
vehement        1
veil    1
veiled  1
veined, 1
veins   1
velocity        4
velvet  3
venci   1
venerable       1
vengeance       1
venne   2
venomous        1
venture 2
verdegris.      1
verdict 1
verdigris       4
verdure 5
verdure,        1
verdure.        1
vere    1
verge   1
verging 5
veri    1
verified        2
verified,       1
verified.]      1
verify  1
vermilion       3
version 2
version,        1
verstummelt".   1
vertebrae       1
vertical        29
verticello      1
very    114
vesicular       1
vessel  1
vessel. 1
vetu    1
vi      2
vicina, 1
vicini  1
victim  1
victim's        1
victors 1
victory 1
victuals        1
vier    1
view    9
view,   2
view.   1
viewed  2
viewing 1
views   7
views,  1
vigour  1
vile,   1
vine    1
vine,   1
vinegar 3
vines   1
violence        1
violent 2
violently       2
violet  1
virgin  2
virtue  1
virtue, 2
virtue. 1
virtue; 1
virtues.        1
virtuous        1
virtù   1
virus,  1
viscid  1
visible 29
visible,        3
visible.        10
visible;        1
visibly 1
visibly.        2
visino  1
visino. 1
vision  6
vision) 1
vision. 1
visit   1
visiva, 1
visual  6
vita    1
vitae   2
vitae,  1
vital   1
vitality        1
vitriol 1
vitriol,        2
vivid   1
vividly 1
vividness       1
voglia  1
voice.  1
vol.    1
volendo 1
voli    1
vollen  1
volumes 3
volumes,        1
volumi  1
volunteers      1
voluto  1
vom     1
von     3
vorgestellte    1
vuoi    1
waist   1
waist,  1
walk    2
walking 5
walking,        1
walks   1
wall    43
wall,   12
wall-painting.  1
wall.   8
wall;   2
walls   16
walls,  2
walls.  2
wall—to 1
walnut  4
walnut. 1
walnuts 2
walnuts,        1
want    25
want,   1
wanted  3
wanting 2
wanting,        1
wanting.        2
wanting;        1
wants   7
wards   1
wares   1
warm    1
warmest 1
warranties      1
warrior 2
warriors.       1
was     118
was.    1
was;    1
wash    4
washed  2
wasted, 1
watchful        1
water   43
water,  12
water-jar.      1
water-power     1
water.  9
water:  1
water;  1
watered 1
watering        1
waters  10
waters, 1
waterworks,     1
wave    2
wavelets,       1
waves   13
waves,  2
waves.  1
waves;  1
wax     6
wax,    3
way     68
way,    9
way.    6
way:    2
way;    3
ways    3
ways.   1
we      139
weak    2
weak?   1
weaken  2
weaker  3
weapon  1
weapons 2
weapons;        1
wear    1
wearied 1
weariness.      1
weary   4
weary,  1
weather 6
weather,        1
weeping,        1
weeping;        1
weigh   3
weight  35
weight, 1
weight. 2
weight; 2
weight] 1
weights 1
well    57
well,   3
well-being      1
well-known      2
well-lighted    1
well-planned    1
well.   4
well;   1
wellknown       1
wells   2
well—as 1
wenn    1
went    4
wept    1
were    101
were,   1
west    5
wet     1
wetted  1
wetted, 1
what    59
what's  1
whatever        9
whatever,       1
wheel,  1
when    237
when,   3
whence  20
whenever        2
where   169
where,  1
whereas 2
wherefore       3
wherever        8
whether 26
whether,        1
which   1076
which,  38
which.  1
whichever       2
which—Pl.       1
while   55
while,  2
whirled 1
whirling        2
whirlpools      2
whirlwinds.     1
white   47
white,  9
white.  4
white;  2
white?  1
whiteness,      1
whiter  7
whiter. 1
whiter; 1
whitest 2
whither 1
whitish 1
who     129
who,    12
whoever 1
whole   87
whole,  4
whole.  5
whole;  2
wholesome       1
wholly  8
wholly, 1
whom    6
whose   13
who—not 1
why     10
wichtigsten     1
wide    16
wide.   1
wide;   1
widely  2
wider   2
widest  4
width   38
wie     1
will    884
will,   5
will.   1
willow  2
willow, 2
win     1
wind    21
wind,   9
wind.   2
window  47
window, 10
window-opening  1
window. 7
window; 3
windows 7
windows.        1
winds   9
winds,  3
winds.  1
winds;  1
wine    4
wine;   1
wings,  1
winner, 1
winter. 3
wire    1
wisdom, 1
wise    2
wish    33
wish,   1
wish.   1
wished  3
wishes  5
wishing 1
with    717
with,   1
with.   1
with;   1
with]   1
withdraw        2
within  43
within, 1
within. 1
within—by       1
without 75
witness 1
wohl    1
wolves  1
wolves, 1
woman   1
woman's 2
women   4
women,  2
wonder  1
wonderful       1
wood    8
wood,   3
wood-cut        1
wood.   1
wood;   1
wooden  5
woods   1
woollen 1
word    20
word,   2
words   20
words,  4
words.  2
words:  1
words;  1
work    70
work,   16
work.   14
work.]  1
work.]. 1
work;   4
worked  8
working 3
works   30
works,  1
works.  4
works—as        1
world   3
world's 1
world.  3
world;  1
worlds, 1
worn    2
worse   1
worse.  1
worth.  1
worthier        1
worthy  3
worthy:—on      1
would   106
would,  3
wound.  1
wounded 3
wounds  1
wrap    2
wrapped 1
wrath   2
wreathed        3
wreathing       1
wrecked 1
wrenching       1
wretched        1
wrinkled,       1
wrinkles        1
wrinkling       1
wrist   9
wrist,  2
wrists, 1
write   5
writer  2
writer; 1
writers 2
writers,        1
writes  2
writes, 2
writing 16
writing.        2
writing.]       1
writing:        1
writings        6
writings,       1
writings.       2
writings?       1
written 60
written,        7
written.        2
written.]       1
written;        1
wrong   4
wrong,  2
wrong.  2
wrong;  1
wrongly 1
wrong—place     1
wrote   13
wusste, 1
x       20
x,      2
x.      2
y       13
y.      1
yard    1
yard.   1
ye      1
year    17
year's  2
year,   2
year.   2
year:   1
year_   1
years   8
years'  1
years,  2
years.  2
yellow  25
yellow, 4
yellow. 3
yellow; 1
yellow].        1
yellower        1
yellowest       1
yellowish       2
yellow—and      1
yet     7
yet,    1
yeux    1
yields  2
you     679
you!)   1
you,    18
you.    6
you?    1
young   6
young,  1
youngest        1
your    189
yours   1
yourself        18
yourself,       1
yourself.       2
yourself;       2
youth   3
youth,  1
youth.  1
youth.] 1
youthful        1
youwant 1
z       10
z.      1
z;      1
zeal    1
zum     1
zvith   1
zwanzig 1
zweite  1
àpieza; 1
è       3
è:      1
ècrit   1
—Experiments    1
—Top    1
—that   1
—when   1
…       13
…'].    1
…,      1
….      1

```
## 1.7 How will the lab work?

- 1.7.3 Important 3

```sh
 
	$ git clone https://github.com/makayel/hadoop-examples-mapreduce.git
	Cloning into 'hadoop-examples-mapreduce'...
	remote: Enumerating objects: 58, done.
	remote: Counting objects: 100% (3/3), done.
	remote: Compressing objects: 100% (3/3), done.
	remote: Total 58 (delta 0), reused 1 (delta 0), pack-reused 55
	Receiving objects: 100% (58/58), 15.37 KiB | 462.00 KiB/s, done.
	Resolving deltas: 100% (7/7), done.
```

## 1.8 Remarkable trees of Paris

 [j.crecel@hadoop-edge01 ~]$ nano trees
 [j.crecel@hadoop-edge01 ~]$ ls
```sh
	Arthur       davini.txt               mapper.py   sudoku.dta  Ulysses
	bonjour.txt  hadoop-dependencies.jar  reducer.py  trees       Vinci
```
 [j.crecel@hadoop-edge01 ~]$ cat trees
```sh
(48.857140829, 2.29533455314);7;Maclura;pomifera;Moraceae;1935;13.0;;Quai Branly, avenue de La Motte-Piquet, avenue de la Bourdonnais, avenue de Suffren;Oranger des Osages;;6;Parc du Champs de Mars
(48.8685686134, 2.31331809304);8;Calocedrus;decurrens;Cupressaceae;1854;20.0;195.0;Cours-la-Reine, avenue Franklin-D.-Roosevelt, avenue Matignon, avenue Gabriel;Cèdre à encens;;11;Jardin des Champs Elysées
(48.8768191638, 2.33210374339);9;Pterocarya;fraxinifolia;Juglandaceae;1862;22.0;330.0;Place d'Estienne-d'Orves;Pérocarya du Caucase;;14;Square Etienne d'Orves
(48.8373323894, 2.40776275516);12;Celtis;australis;Cannabaceae;1906;16.0;295.0;27, boulevard Soult;Micocoulier de Provence;;16;Avenue 27 boulevard Soult
(48.8341842636, 2.46130493573);12;Quercus;petraea;Fagaceae;1784;30.0;430.0;route ronde des Minimes;Chêne rouvre;;19;Bois de Vincennes (lac des minimes)
(48.8325900983, 2.41116455985);12;Platanus;x acerifolia;Platanaceae;1860;45.0;405.0;Ile de Bercy;Platane commun;;21;Bois de Vincennes (Ile de Bercy)
(48.8226749117, 2.33869560229);14;Platanus;x acerifolia;Platanaceae;1840;40.0;580.0;Bd Jourdan, avenue Reille, rue Gazan, rue de la Cité‚-Universitaire, rue Nansouty;Platane commun;;26;Parc Montsouris
(48.8428118006, 2.2972574926);15;Alnus;glutinosa;Betulaceae;1933;16.0;220.0;Rue Th‚ophraste-Renaudot, rue L‚on-Lhermitte, rue Jean Formig‚, rue du Docteur Jacquem;Aulne glutineux;;28;Square Saint Lambert
(48.8717782491, 2.27973325759);16;Aesculus;hippocastanum;Sapindaceae;;30.0;505.0;Avenue Foch;Marronnier d'Inde;;30;Avenue Foch
(48.8802898189, 2.38157469859);19;Ginkgo;biloba;Ginkgoaceae;1913;33.0;230.0;Rue Manin, rue Botzaris;Arbre aux quarante écus;;46;Parc des Buttes Chaumont
(48.8820015094, 2.39836942721);19;Fraxinus;excelsior;Oleaceae;;30.0;365.0;Boulevard d'Algérie;Frêne commun;;52;Square de la Butte du Chapeau Rouge
(48.846044762, 2.2529555706);16;Ailanthus;giraldii;Simaroubaceae;;35.0;460.0;3 avenue de la Porte d'Auteuil, 1 avenue Gordon Benett;Ailanthe;;53;Jardin des Serres d'Auteuil
(48.8606198209, 2.2599223737);16;Taxodium;distichum;Taxodiaceae;1862;35.0;350.0;Berge du lac Inférieur;Cyprés chauve;;56;Bois de Boulogne (Berge du lac inférieur)
(48.8232165418, 2.46016871078);12;Diospyros;kaki;Ebenaceae;;12.0;160.0;Route de la Ferme, route de la Pyramide;Kaki;;58;Jardin de l' Ecole Du Breuil
(48.8764503804, 2.25765244347);16;Sequoiadendron;giganteum;Taxodiaceae;1850;30.0;;;Séquoia géant;;59;Bois de Boulogne (Portes Saint james)
(48.8691485018, 2.27224125103);16;Gymnocladus;dioicus;Fabaceae;;10.0;162.0;;Chicot du Canada;;61;Square Schumann
(48.8615768444, 2.25902702441);16;Fagus;sylvatica;Fagaceae;1857;10.0;200.0;;Hêtre pleureur;Pendula;63;Bois de Boulogne (petite île du Lac Inférieur)
(48.8633555664, 2.26174532022);16;Pterocarya;fraxinifolia;Juglandaceae;1882;27.0;400.0;;Pérocarya du Caucase;;65;Bois de Boulogne (Berge du lac inférieur)
(48.8646024472, 2.25171449183);16;Sequoiadendron;giganteum;Taxodiaceae;1872;;655.0;Route de la Grande Cascade, carrefour de la Croix Catelan;Séquoia géant;;67;Bois de Boulogne (Pré Catelan)
(48.865022534, 2.2538285063);16;Pinus;nigra;Pinaceae;;30.0;250.0;Route de la Grande Cascade, carrefour de la Croix Catelan;Pin noir;;69;Bois de Boulogne (Pré Catelan)
(48.8704017043, 2.24852577475);16;Platanus;orientalis;Platanaceae;1843;26.0;340.0;Allée de Longchamp, route de Sèvres à Neuilly;Platane d'Orient;;73;Bois de Boulogne (Bagatelle)
(48.8347628794, 2.42029690936);12;Zelkova;serrata;Ulmaceae;1872;18.0;240.0;;Zelkova du Japon;;83;Bois de Vincennes (Ecole chiens guide d'aveugle)
(48.8333849101, 2.41261756721);12;Juglans;nigra;Juglandaceae;1845;28.0;570.0;route de la ceinture du Lac Daumesnil;Noyer noir;;85;Bois de Vincennes (Lac Daumesnil/porte Dorée)
(48.8324049718, 2.41169855654);12;Taxodium;distichum;Taxodiaceae;1930;20.0;270.0;Ile de Bercy;Cyprés chauve;;87;Bois de Vincennes (Ile de Bercy)
(48.8213214388, 2.45537251962);12;Pinus;bungeana;Pinaceae;;10.0;50.0;Route de la Ferme, route de la Pyramide;Pin Napoléon;;95;Arboretum Ecole du Breuil
(48.8204495642, 2.44579219199);12;Pinus;nigra;Pinaceae;1870;25.0;248.0;route de la Tourelle, route du Point de Vue;Pin noir;Austriaca;97;Bois de Vincennes (lac de gravelle)
(48.8520958913, 2.34740754195);5;Robinia;pseudoacacia;Fabaceae;1601;11.0;385.0;Quai de Montebello, rue Lagrange, rue Saint-Julien-le-Pauvre;Robinier faux-acacia;;4;Square Viviani
(48.8578717375, 2.29706549763);7;Eucommia;ulmoides;Eucomiaceae;;12.0;190.0;Quai Branly, avenue de La Motte-Piquet, avenue de la Bourdonnais, avenue de Suffren;Arbre à gutta-percha;;7;Parc du Champs de Mars
(48.8792159582, 2.30640768208);8;Ginkgo;biloba;Ginkgoaceae;1879;22.0;283.0;Boulevard de Courcelles, avenue V‚lasquez, avenue Van-Dyck, avenue Ruysdael;Arbre aux quarante écus;;10;Parc Monceau
(48.8669690843, 2.31951408752);8;Sequoiadendron;giganteum;Taxodiaceae;1850;20.0;320.0;Cours-la-Reine, avenue Franklin-D.-Roosevelt, avenue Matignon, avenue Gabriel;Séquoia géant;;12;Jardin des Champs Elysées
(48.8353848188, 2.38157245444);12;Platanus;x acerifolia;Platanaceae;;35.0;510.0;Rue Paul-Belmondo, rue Joseph-Kessel, rue de l'Ambroise, rue François-Truffaut;Platane commun;;17;Parc de Bercy
(48.8330496955, 2.35078878768);13;Aesculus;hippocastanum;Sapindaceae;1894;18.0;355.0;Rue Croulebarbe, rue Corvisart, rue Emile-Deslandres, rue des Cordelières;Marronnier d'Inde;;23;Square René Le Gall
(48.8224956954, 2.3366608746);14;Fagus;sylvatica;Fagaceae;;30.0;370.0;Bd Jourdan, avenue Reille, rue Gazan, rue de la Cité‚-Universitaire, rue Nansouty;Hêtre pourpre;Purpurea;25;Parc Montsouris
(48.8220238534, 2.33628540112);14;Sequoia;sempervirens;Taxodiaceae;1935;30.0;335.0;Bd Jourdan, avenue Reille, rue Gazan, rue de la Cité‚-Universitaire, rue Nansouty;Séquoia sempervirent;;27;Parc Montsouris
(48.8814628758, 2.38367383179);19;Styphnolobium;japonicum;Fabaceae;1873;10.0;335.0;Rue Manin, rue Botzaris;Sophora du Japon;;44;Parc des Buttes Chaumont
(48.8803986732, 2.38129958306);19;Platanus;orientalis;Platanaceae;1862;34.0;670.0;Rue Manin, rue Botzaris;Platane d'Orient;;45;Parc des Buttes Chaumont
(48.8619346483, 2.39870061217);20;Acer;monspessulanum;Sapindacaees;1833;12.0;225.0;Rue du repos, rue des Rondeaux;Erable de Montpellier;;48;Cimetière du Père Lachaise
(48.879759998, 2.38064802989);19;Sequoiadendron;giganteum;Taxodiaceae;;35.0;470.0;Rue Manin, rue Botzaris;Séquoia géant;;57;Parc des Buttes Chaumont
(48.8640166469, 2.26774597209);16;Fagus;sylvatica;Fagaceae;;18.0;300.0;;Hêtre pourpre;Purpurea;60;Stade Muette
(48.8647824278, 2.25120424857);16;Diospyros;kaki;Ebenaceae;1897;14.0;145.0;Route de la Grande Cascade, carrefour de la Croix Catelan;Kaki;;68;Bois de Boulogne (Pré Catelan)
(48.8693939056, 2.24776773334);16;Sequoiadendron;giganteum;Taxodiaceae;1850;30.0;490.0;Allée de Longchamp, route de Sèvres à Neuilly;Séquoia géant;;72;Bois de Boulogne (Bagatelle)
(48.867043584, 2.25320074406);16;Platanus;x acerifolia;Platanaceae;1872;40.0;520.0;Route du Lac à Bagatelle;Platane commun;;74;Bois de Boulogne (Route du Lac à Bagatelle)
(48.8630909172, 2.24159242682);16;Pinus;nigra laricio;Pinaceae;1882;30.0;240.0;All‚e de Longchamp, carrefour des cascades;Pin de Corse;;76;Bois de Boulogne (réservoir de la cascade)
(48.8632834941, 2.24066981564);16;Taxodium;distichum;Taxodiaceae;1859;30.0;290.0;Allée de Longchamp, carrefour des cascades;Cyprés chauve;;77;Bois de Boulogne (Grande Cascade)
(48.8400020891, 2.46422657197);12;Acer;cappadocicum;Sapindaceae;1900;16.0;280.0;avenue de la Belle Gabrielle;Erable de Cappadoce;;78;Bois de Vincennes (pelouse de Fontenay)
(48.8394165343, 2.43360205128);12;Liriodendron;tulipifera;Magnoliaceae;1862;35.0;305.0;avenue Daumesnil, Esplanade du Château de Vincennes;Tulipier de Virginie;;81;Bois de Vincennes (square Carnot)
(48.8319232533, 2.41202933239);12;Liriodendron;tulipifera;Magnoliaceae;1930;22.0;205.0;Ile de Bercy;Tulipier de Virginie;;88;Bois de Vincennes (Ile de Bercy)
(48.8320684332, 2.41182825531);12;Taxus;baccata;Taxaceae;1870;5.0;140.0;Ile de Bercy;If commun;;89;Bois de Vincennes (Ile de Bercy)
(48.8292071873, 2.41301158121);12;Platanus;x acerifolia;Platanaceae;1871;25.0;490.0;route de la ceinture du Lac Daumesnil;Platane commun;;92;Bois de Vincennes (lac daumesnil)
(48.8400754064, 2.43381509843);12;Diospyros;virginiana;Ebenaceae;1875;14.0;180.0;avenue Daumesnil, Esplanade du Château de Vincennes;Plaqueminier de Virginie;;94;Bois de Vincennes (square Carnot)
(48.8183933679, 2.43791766754);12;Quercus;ilex;Fagaceae;1860;15.0;;route de Gravelle, route du Mar‚chal Leclerc (Saint Maurice);Chêne vert;;98;Bois de Vincennes (pente de Gravelle)
(48.8557581795, 2.35399582218);4;Ulmus;carpinifolia;Ulmaceae;1935;15.0;180.0;Place St Gervais;Orme champêtre;;2;Place Saint Gervais
(48.8453050031, 2.35307565328);5;Fagus;sylvatica;Fagaceae;1905;2.0;72.0;Rue des Arênes, rue de Navarre, rue Monge;Faux de Verzy;Tortuosa;3;Square des Arènes de Lutèce
(48.8618464812, 2.37910176561);11;Corylus;colurna;Betulaceae;1879;20.0;245.0;Rue Lacharrière, rue Rochebrune, rue du Général-Guilhem, rue du Général-Blaise;Noisetier de Byzance;;15;Square Maurice Gardette
(48.8420426954, 2.43848438671);12;Fagus;sylvatica;Fagaceae;1895;23.0;370.0;Cours Marigny;Hêtre pourpre;Purpurea;18;Bois de Vincennes (Cours Marigny)
(48.8201249835, 2.44524393613);12;Cedrus;libanii;Pinaceae;1829;30.0;440.0;route de la Tourelle, route du Point de Vue;Cèdre du Liban;;22;Bois de Vincennes (lac de Gravelle)
(48.8471789821, 2.25293802515);16;Quercus;suber;Fagaceae;1895;10.0;180.0;3 avenue de la Porte d'Auteuil, 1 avenue Gordon Benett;Chêne liège;;32;Jardin des Serres d'Auteuil
(48.8450859307, 2.26948936839);16;Broussonetia;papyrifera;Moraceae;;12.0;190.0;Rue Mirabeau, avenue de Versailles;Murier à papier;;33;Parc Sainte Perinne
(48.8634848878, 2.2403752961);16;Cedrus;libanii;Pinaceae;1862;30.0;460.0;All‚e de Longchamp, carrefour des cascades;Cèdre du Liban;;37;Bois de Boulogne (réservoir de la grande cascade)
(48.8845880534, 2.34391859224);18;Platanus;orientalis;Platanaceae;1857;27.0;470.0;Place Saint-Pierre, rue Ronsard, rue Paul-Albert, rue Maurice Utrillo;Platane d'Orient;;42;Square Louise Michel
(48.8830346813, 2.37007425143);19;Tilia;tomentosa;Malvaceae;1945;20.0;205.0;Place Stalingrad;Tilleul argenté;;43;Place de la bataille de Stalingrad
(48.85646631, 2.39469777758);20;Platanus;x acerifolia;Platanaceae;1880;20.0;395.0;148 boulevard de Charonne;Platane commun;;51;Alignement 148 boulevard de Charonne
(48.8471653404, 2.25199572129);16;Pterocarya;stenoptera;Juglandaceae;1905;30.0;530.0;3 avenue de la Porte d'Auteuil, 1 avenue Gordon Benett;Ptérocarya de Chine;;54;Jardin des Serres d'Auteuil
(48.867221687, 2.27027693483);16;Cedrus;atlantica;Pinaceae;;6.0;195.0;;Cèdre bleu de l'Atlas ple;Glauca pendula;62;Square Debussy
(48.8731203887, 2.24884917245);16;Fagus;sylvatica;Fagaceae;1868;15.0;230.0;Allée de Longchamp, route de Sèvres à Neuilly;Hêtre pleureur;Pendula;70;Bois de Boulogne (Bagatelle)
(48.8732545226, 2.24886543775);16;Davidia;involucrata;Cornaceae;1906;12.0;120.0;Allée de Longchamp, route de Sèvres à Neuilly;Arbre aux pochettes;;71;Bois de Boulogne (Bagatelle)
(48.8433252639, 2.4497117757);12;Quercus;petraea;Fagaceae;1815;31.0;450.0;;Chêne rouve;;80;Bois de Vincennes (fort neuf)
(48.8323806372, 2.41052012477);12;Platanus;x acerifolia;Platanaceae;1860;42.0;405.0;Ile de Bercy;Platane commun;;90;Bois de Vincennes (Ile de Bercy)
(48.8314334738, 2.4115101993);12;Diospyros;virginiana;Ebenaceae;1935;12.0;;Ile de Bercy;Plaqueminier de Virginie;;93;Bois de Vincennes (Ile de Bercy)
(48.8210086122, 2.45551492936);12;Pinus;coulteri;Pinaceae;;14.0;225.0;Route de la Ferme, route de la Pyramide;Pin aux grands cônes;;96;Arboretum Ecole du Breuil
(48.8785456147, 2.30757576047);8;Platanus;orientalis;Platanaceae;1814;31.0;700.0;Boulevard de Courcelles, avenue V‚lasquez, avenue Van-Dyck, avenue Ruysdael;Platane d'Orient;;9;Parc Monceau
(48.8652536076, 2.31333976248);8;Platanus;orientalis;Platanaceae;1900;20.0;480.0;Cours-la-Reine, avenue Franklin-D.-Roosevelt, avenue Matignon, avenue Gabriel;Platane d'Orient;;13;Jardin des Champs Elysées
(48.8476260928, 2.25278179131);16;Ginkgo;biloba;Ginkgoaceae;1895;25.0;395.0;3 avenue de la Porte d'Auteuil, 1 avenue Gordon Benett;Arbre aux quarante écus;;31;Jardin des Serres d'Auteuil
(48.861574817, 2.2910717819);16;Corylus;colurna;Betulaceae;;20.0;260.0;Place du Trocad‚ro et du 11 Novembre, rue Benjamin Franklin, avenue Albert de Mun;Noisetier de Byzance;;34;Jardin du Trocadéro
(48.8708601366, 2.24769299518);16;Taxus;baccata;Taxaceae;1772;13.0;235.0;Allée de Longchamp, route de Sèvres à Neuilly;If commun;;36;Bois de Boulogne (Bagatelle)
(48.8646850734, 2.25360607406);16;Fagus;sylvatica;Fagaceae;1782;30.0;558.0;Route de la Grande Cascade, carrefour de la Croix Catelan;Hêtre pourpre;Purpurea;38;Bois de Boulogne (Pré Catelan)
(48.8880577555, 2.31595908796);17;Platanus;x acerifolia;Platanaceae;1840;30.0;595.0;Place Charles Filion, rue Cardinet;Platane commun;;41;Square des Batignolles
(48.8597396934, 2.39997847741);20;Aesculus;hippocastanum;Sapindaceae;;22.0;345.0;Rue du repos, rue des Rondeaux;Marronnier d'Inde;;47;Cimetière du Père Lachaise
(48.8622517606, 2.26098883991);16;Ginkgo;biloba;Ginkgoaceae;1893;18.0;215.0;;Arbre aux quarante écus;;64;Bois de Boulogne (Berge du lac inférieur)
(48.8336849895, 2.42111102704);12;Ginkgo;biloba;Ginkgoaceae;1865;25.0;255.0;;Arbre aux quarante écus;;84;Bois de Vincennes (Ecole chiens guide d'aveugle)
(48.8648376291, 2.36062929978);3;Corylus;colurna;Betulaceae;1882;20.0;210.0;Rue du Temple, rue de Bretagne, Rue Perrée, rue Eugène-Spuller;Noisetier de Byzance;;1;Square du Temple
(48.856902513, 2.33666989768);6;Catalpa;bignonioides;Bignoniaceae;;15.0;260.0;Rue de Seine, rue Mazarine;Catalpa commun;;5;Square Gabriel Pierné
(48.8577766649, 2.29329076205);7;Platanus;orientalis;Platanaceae;1814;20.0;700.0;Quai Branly, avenue de La Motte-Piquet, avenue de la Bourdonnais, avenue de Suffren;Platane d'Orient;;8;Parc du Champs de Mars
(48.8399672948, 2.43375148978);12;Fagus;sylvatica;Fagaceae;1865;20.0;530.0;avenue Daumesnil, Esplanade du Château de Vincennes;Hêtre pleureur;Pendula;20;Bois de Vincennes (square Carnot)
(48.827737189, 2.3592096955);13;Cedrus;atlantica;Pinaceae;1939;25.0;350.0;128-160 avenue de Choisy, rue Georges-Eastman, rue Charles-Moureu, rue du Docteur-Magn;Cèdre bleu de l'Atlas;Glauca;24;Parc de Choisy
(48.8723867386, 2.27912885453);16;Zelkova;carpinifolia;Ulmaceae;1852;30.0;395.0;Avenue Foch;Faux orme de Sibérie;;29;Avenue Foch
(48.8619170093, 2.2924448277);16;Paulownia;tomentosa;Paulowniaceae;;20.0;420.0;Place du Trocad‚ro et du 11 Novembre, rue Benjamin Franklin, avenue Albert de Mun;Paulownia;;35;Jardin du Trocadéro
(48.8716117578, 2.24933653506);16;Araucaria;araucana;Araucariaceae;1907;9.0;140.0;Allée de Longchamp, route de Sèvres à Neuilly;Désespoir du singe;;39;Bois de Boulogne (Bagatelle)
(48.8691433358, 2.24587597613);16;Platanus;x acerifolia;Platanaceae;1847;40.0;480.0;Allée de Longchamp, route de Sèvres à Neuilly;Platane commun;;40;Bois de Boulogne (Bagatelle)
(48.8661956075, 2.26238964912);16;Platanus;orientalis;Platanaceae;1859;25.0;375.0;Ile du lac inférieur;Platane d'Orient;;49;Bois de Boulogne (île du lac inférieur)
(48.8215800145, 2.45494779675);12;Zelkova;carpinifolia;Ulmaceae;;12.0;245.0;Route de la Ferme, route de la Pyramide;Faux orme de Sibérie;;50;Arboretum de Ecole du Breuil
(48.8727584235, 2.2873548507);16;Platanus;x acerifolia;Platanaceae;1852;30.0;525.0;Avenue Foch;Platane commun;;55;Avenue Foch
(48.8588189763, 2.25832952119);16;Magnolia;grandiflora;Magnoliaceae;1863;12.0;;Allée de Longchamp, carrefour des cascades;Magnolia à grandes fleurs;;66;Bois de Boulogne (Berge du lac inférieur)
(48.86260617, 2.23782412563);16;Zelkova;carpinifolia;Ulmaceae;1896;16.0;260.0;;Faux orme de Sibérie;;75;Bois de Boulogne (Moulin de Longchamp)
(48.8395160905, 2.43350820893);12;Platanus;x acerifolia;Platanaceae;1918;32.0;570.0;avenue Daumesnil, Esplanade du Château de Vincennes;Platane commun;;82;Bois de Vincennes (Square Carnot)
(48.833545551, 2.41033694606);12;Platanus;orientalis;Platanaceae;1860;22.0;475.0;route de la ceinture du Lac Daumesnil;Platane d'Orient;;86;Bois de Vincennes (Lac Daumesnil/porte Dorée)
(48.8302532096, 2.41400587444);12;Acer;opalus;Sapindaceae;1870;15.0;160.0;Ile de Bercy;Erable d'Italie;;91;Bois de Vincennes (Ile de Bercy)
```

 [j.crecel@hadoop-edge01 ~]$ hdfs dfs -ls data
```sh
	Found 1 items
	drwxr-xr-x   - j.crecel j.crecel          0 2021-09-29 18:08 data/10GB-sort-input
```
 [j.crecel@hadoop-edge01 ~]$ hdfs dfs -copyFromLocal trees 
 [j.crecel@hadoop-edge01 ~]$ hdfs dfs -ls 
```sh
	Found 14 items
	drwx------   - j.crecel j.crecel          0 2021-10-01 08:00 .Trash
	drwx------   - j.crecel j.crecel          0 2021-10-01 03:15 .staging
	-rw-r--r--   3 j.crecel j.crecel     656215 2021-09-29 19:34 Arthur
	-rw-r--r--   3 j.crecel j.crecel     541173 2021-09-29 19:35 Ulysses
	-rw-r--r--   3 j.crecel j.crecel     601122 2021-09-29 19:35 Vinci
	-rw--w--w-   3 j.crecel j.crecel         17 2021-09-24 09:36 bonjour.txt
	drwxr-xr-x   - j.crecel j.crecel          0 2021-10-01 11:02 data
	-rw-r--r--   3 j.crecel j.crecel     601122 2021-10-01 03:10 davini.txt
	drwxr-xr-x   - j.crecel j.crecel          0 2021-09-24 08:33 dossier
	-rw-r--r--   3 j.crecel j.crecel   58977112 2021-10-01 03:04 hadoop-dependencies.jar
	drwxr-xr-x   - j.crecel j.crecel          0 2021-10-01 10:59 paris
	drwxr-xr-x   - j.crecel j.crecel          0 2021-10-01 06:02 raw
	-rw-r--r--   3 j.crecel j.crecel      16553 2021-10-01 11:59 trees
	drwxr-xr-x   - j.crecel j.crecel          0 2021-10-01 03:15 wordcount
```

 	[j.crecel@hadoop-edge01 ~]$ hdfs dfs -rm Arthur
 	[j.crecel@hadoop-edge01 ~]$ hdfs dfs -rm Ulysses
	 [j.crecel@hadoop-edge01 ~]$ hdfs dfs -rm Vinci
 	[j.crecel@hadoop-edge01 ~]$ hdfs dfs -rm bonjour.txt
 	[j.crecel@hadoop-edge01 ~]$ hdfs dfs -rm -r data
 	[j.crecel@hadoop-edge01 ~]$ hdfs dfs -rm davini.txt
 	[j.crecel@hadoop-edge01 ~]$ hdfs dfs -rm -r dossier
 	[j.crecel@hadoop-edge01 ~]$ hdfs dfs -rm -r paris
 	[j.crecel@hadoop-edge01 ~]$ hdfs dfs -rm -r raw
 	[j.crecel@hadoop-edge01 ~]$ hdfs dfs -rm -r  wordcount
 	[j.crecel@hadoop-edge01 ~]$ hdfs dfs -ls
```sh
	Found 4 items
	drwx------   - j.crecel j.crecel          0 2021-10-01 12:03 .Trash
	drwx------   - j.crecel j.crecel          0 2021-10-01 03:15 .staging
	-rw-r--r--   3 j.crecel j.crecel   58977112 2021-10-01 03:04 hadoop-dependencies.jar
	-rw-r--r--   3 j.crecel j.crecel      16553 2021-10-01 11:59 trees
```
 [j.crecel@hadoop-edge01 ~]$ hdfs dfs -mv trees trees.csv

 [j.crecel@hadoop-edge01 ~]$ hdfs dfs -ls
```sh
	Found 4 items
	drwx------   - j.crecel j.crecel          0 2021-10-01 12:03 .Trash
	drwx------   - j.crecel j.crecel          0 2021-10-01 03:15 .staging
	-rw-r--r--   3 j.crecel j.crecel   58977112 2021-10-01 03:04 hadoop-dependencies.jar
	-rw-r--r--   3 j.crecel j.crecel      16553 2021-10-01 11:59 tress.csv
```

- 1.8.1 Districts containing trees 
                       *Start the wordcount job:
 [j.crecel@hadoop-edge01 ~]$ yarn jar /usr/odp/current/hadoop-mapreduce-client/hadoop-mapreduce-examples.jar \wordcount /user/j.crecel/trees.csv                 /user/j.crecel/wordcount

```sh
	21/10/01 13:13:56 INFO impl.TimelineReaderClientImpl: Initialized TimelineReader URI=https://hadoop-master03.efrei.online:8199/ws/v2/timeline/, 	clusterId=yarn-cluster
	21/10/01 13:13:56 INFO client.AHSProxy: Connecting to Application History server at hadoop-master03.efrei.online/163.172.102.23:10200
	21/10/01 13:13:56 INFO hdfs.DFSClient: Created token for j.crecel: HDFS_DELEGATION_TOKEN owner=j.crecel@EFREI.ONLINE, renewer=yarn, realUser=, 	issueDate=1633086836571, maxDate=1633691636571, sequenceNumber=1580, masterKeyId=44 on ha-hdfs:efrei
	21/10/01 13:13:56 INFO security.TokenCache: Got dt for hdfs://efrei; Kind: HDFS_DELEGATION_TOKEN, Service: ha-hdfs:efrei, Ident: (token for 	j.crecel: HDFS_DELEGATION_TOKEN owner=j.crecel@EFREI.ONLINE, renewer=yarn, realUser=, issueDate=1633086836571, maxDate=1633691636571, 	sequenceNumber=1580, masterKeyId=44)
	21/10/01 13:13:56 INFO client.ConfiguredRMFailoverProxyProvider: Failing over to rm2
	21/10/01 13:13:56 INFO mapreduce.JobResourceUploader: Disabling Erasure Coding for path: /user/j.crecel/.staging/job_1630864376208_1228
	21/10/01 13:13:56 INFO input.FileInputFormat: Total input files to process : 1
	21/10/01 13:13:57 INFO mapreduce.JobSubmitter: number of splits:1
	21/10/01 13:13:57 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1630864376208_1228
	21/10/01 13:13:57 INFO mapreduce.JobSubmitter: Executing with tokens: [Kind: HDFS_DELEGATION_TOKEN, Service: ha-hdfs:efrei, Ident: (token for 	j.crecel: HDFS_DELEGATION_TOKEN owner=j.crecel@EFREI.ONLINE, renewer=yarn, realUser=, issueDate=1633086836571, maxDate=1633691636571, 	sequenceNumber=1580, masterKeyId=44)]
	21/10/01 13:13:57 INFO conf.Configuration: found resource resource-types.xml at file:/etc/hadoop/1.0.3.0-223/0/resource-types.xml
	21/10/01 13:13:57 INFO impl.TimelineClientImpl: Timeline service address: hadoop-master03.efrei.online:8190
	21/10/01 13:13:57 INFO impl.YarnClientImpl: Submitted application application_1630864376208_1228
	21/10/01 13:13:57 INFO mapreduce.Job: The url to track the job: https://hadoop-master02.efrei.online:8090/proxy/application_1630864376208_1228/
	21/10/01 13:13:57 INFO mapreduce.Job: Running job: job_1630864376208_1228
	21/10/01 13:14:06 INFO mapreduce.Job: Job job_1630864376208_1228 running in uber mode : false
	21/10/01 13:14:06 INFO mapreduce.Job:  map 0% reduce 0%
	21/10/01 13:14:13 INFO mapreduce.Job:  map 100% reduce 0%
	21/10/01 13:14:18 INFO mapreduce.Job:  map 100% reduce 100%
	21/10/01 13:14:18 INFO mapreduce.Job: Job job_1630864376208_1228 completed successfully
	21/10/01 13:14:18 INFO mapreduce.Job: Counters: 54
        File System Counters
                FILE: Number of bytes read=16416
                FILE: Number of bytes written=559079
                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
                HDFS: Number of bytes read=16662
                HDFS: Number of bytes written=14118
                HDFS: Number of read operations=8
                HDFS: Number of large read operations=0
                HDFS: Number of write operations=2
                HDFS: Number of bytes read erasure-coded=0
        Job Counters
                Launched map tasks=1
                Launched reduce tasks=1
                Data-local map tasks=1
                Total time spent by all maps in occupied slots (ms)=13506
                Total time spent by all reduces in occupied slots (ms)=10100
                Total time spent by all map tasks (ms)=4502
                Total time spent by all reduce tasks (ms)=2525
                Total vcore-milliseconds taken by all map tasks=4502
                Total vcore-milliseconds taken by all reduce tasks=2525
                Total megabyte-milliseconds taken by all map tasks=6915072
                Total megabyte-milliseconds taken by all reduce tasks=5171200
        Map-Reduce Framework
                Map input records=97
                Map output records=1216
                Map output bytes=21417
                Map output materialized bytes=16416
                Input split bytes=109
                Combine input records=1216
                Combine output records=576
                Reduce input groups=576
                Reduce shuffle bytes=16416
                Reduce input records=576
                Reduce output records=576
                Spilled Records=1152
                Shuffled Maps =1
                Failed Shuffles=0
                Merged Map outputs=1
                GC time elapsed (ms)=188
                CPU time spent (ms)=2600
                Physical memory (bytes) snapshot=1446936576
                Virtual memory (bytes) snapshot=7280664576
                Total committed heap usage (bytes)=1508376576
                Peak Map Physical memory (bytes)=1156476928
                Peak Map Virtual memory (bytes)=3400859648
                Peak Reduce Physical memory (bytes)=290459648
                Peak Reduce Virtual memory (bytes)=3879804928
        Shuffle Errors
                BAD_ID=0
                CONNECTION=0
                IO_ERROR=0
                WRONG_LENGTH=0
                WRONG_MAP=0
                WRONG_REDUCE=0
        File Input Format Counters
                Bytes Read=16553
        File Output Format Counters
                Bytes Written=14118
```
 [j.crecel@hadoop-edge01 ~]$ hdfs dfs -cat  /user/j.crecel/wordcount/part-r-00000
```sh
(48.8183933679, 1
(48.8201249835, 1
(48.8204495642, 1
(48.8210086122, 1
(48.8213214388, 1
(48.8215800145, 1
(48.8220238534, 1
(48.8224956954, 1
(48.8226749117, 1
(48.8232165418, 1
(48.827737189,  1
(48.8292071873, 1
(48.8302532096, 1
(48.8314334738, 1
(48.8319232533, 1
(48.8320684332, 1
(48.8323806372, 1
(48.8324049718, 1
(48.8325900983, 1
(48.8330496955, 1
(48.8333849101, 1
(48.833545551,  1
(48.8336849895, 1
(48.8341842636, 1
(48.8347628794, 1
(48.8353848188, 1
(48.8373323894, 1
(48.8394165343, 1
(48.8395160905, 1
(48.8399672948, 1
(48.8400020891, 1
(48.8400754064, 1
(48.8420426954, 1
(48.8428118006, 1
(48.8433252639, 1
(48.8450859307, 1
(48.8453050031, 1
(48.846044762,  1
(48.8471653404, 1
(48.8471789821, 1
(48.8476260928, 1
(48.8520958913, 1
(48.8557581795, 1
(48.85646631,   1
(48.856902513,  1
(48.857140829,  1
(48.8577766649, 1
(48.8578717375, 1
(48.8588189763, 1
(48.8597396934, 1
(48.8606198209, 1
(48.861574817,  1
(48.8615768444, 1
(48.8618464812, 1
(48.8619170093, 1
(48.8619346483, 1
(48.8622517606, 1
(48.86260617,   1
(48.8630909172, 1
(48.8632834941, 1
(48.8633555664, 1
(48.8634848878, 1
(48.8640166469, 1
(48.8646024472, 1
(48.8646850734, 1
(48.8647824278, 1
(48.8648376291, 1
(48.865022534,  1
(48.8652536076, 1
(48.8661956075, 1
(48.8669690843, 1
(48.867043584,  1
(48.867221687,  1
(48.8685686134, 1
(48.8691433358, 1
(48.8691485018, 1
(48.8693939056, 1
(48.8704017043, 1
(48.8708601366, 1
(48.8716117578, 1
(48.8717782491, 1
(48.8723867386, 1
(48.8727584235, 1
(48.8731203887, 1
(48.8732545226, 1
(48.8764503804, 1
(48.8768191638, 1
(48.8785456147, 1
(48.8792159582, 1
(48.879759998,  1
(48.8802898189, 1
(48.8803986732, 1
(48.8814628758, 1
(48.8820015094, 1
(48.8830346813, 1
(48.8845880534, 1
(48.8880577555, 1
(Bagatelle)     7
(Berge  4
(Cours  1
(Ecole  2
(Grande 1
(Ile    7
(Lac    2
(Moulin 1
(Portes 1
(Pré    4
(Route  1
(Saint  1
(Square 1
(fort   1
(lac    4
(pelouse        1
(pente  1
(petite 1
(réservoir      2
(square 3
(île    1
1       4
11      2
148     1
2.23782412563);16;Zelkova;carpinifolia;Ulmaceae;1896;16.0;260.0;;Faux   1
2.2403752961);16;Cedrus;libanii;Pinaceae;1862;30.0;460.0;All‚e  1
2.24066981564);16;Taxodium;distichum;Taxodiaceae;1859;30.0;290.0;Allée  1
2.24159242682);16;Pinus;nigra   1
2.24587597613);16;Platanus;x    1
2.24769299518);16;Taxus;baccata;Taxaceae;1772;13.0;235.0;Allée  1
2.24776773334);16;Sequoiadendron;giganteum;Taxodiaceae;1850;30.0;490.0;Allée    1
2.24852577475);16;Platanus;orientalis;Platanaceae;1843;26.0;340.0;Allée 1
2.24884917245);16;Fagus;sylvatica;Fagaceae;1868;15.0;230.0;Allée        1
2.24886543775);16;Davidia;involucrata;Cornaceae;1906;12.0;120.0;Allée   1
2.24933653506);16;Araucaria;araucana;Araucariaceae;1907;9.0;140.0;Allée 1
2.25120424857);16;Diospyros;kaki;Ebenaceae;1897;14.0;145.0;Route        1
2.25171449183);16;Sequoiadendron;giganteum;Taxodiaceae;1872;;655.0;Route        1
2.25199572129);16;Pterocarya;stenoptera;Juglandaceae;1905;30.0;530.0;3  1
2.25278179131);16;Ginkgo;biloba;Ginkgoaceae;1895;25.0;395.0;3   1
2.25293802515);16;Quercus;suber;Fagaceae;1895;10.0;180.0;3      1
2.2529555706);16;Ailanthus;giraldii;Simaroubaceae;;35.0;460.0;3 1
2.25320074406);16;Platanus;x    1
2.25360607406);16;Fagus;sylvatica;Fagaceae;1782;30.0;558.0;Route        1
2.2538285063);16;Pinus;nigra;Pinaceae;;30.0;250.0;Route 1
2.25765244347);16;Sequoiadendron;giganteum;Taxodiaceae;1850;30.0;;;Séquoia      1
2.25832952119);16;Magnolia;grandiflora;Magnoliaceae;1863;12.0;;Allée    1
2.25902702441);16;Fagus;sylvatica;Fagaceae;1857;10.0;200.0;;Hêtre       1
2.2599223737);16;Taxodium;distichum;Taxodiaceae;1862;35.0;350.0;Berge   1
2.26098883991);16;Ginkgo;biloba;Ginkgoaceae;1893;18.0;215.0;;Arbre      1
2.26174532022);16;Pterocarya;fraxinifolia;Juglandaceae;1882;27.0;400.0;;Pérocarya      1
2.26238964912);16;Platanus;orientalis;Platanaceae;1859;25.0;375.0;Ile   1
2.26774597209);16;Fagus;sylvatica;Fagaceae;;18.0;300.0;;Hêtre   1
2.26948936839);16;Broussonetia;papyrifera;Moraceae;;12.0;190.0;Rue      1
2.27027693483);16;Cedrus;atlantica;Pinaceae;;6.0;195.0;;Cèdre   1
2.27224125103);16;Gymnocladus;dioicus;Fabaceae;;10.0;162.0;;Chicot      1
2.27912885453);16;Zelkova;carpinifolia;Ulmaceae;1852;30.0;395.0;Avenue  1
2.27973325759);16;Aesculus;hippocastanum;Sapindaceae;;30.0;505.0;Avenue 1
2.2873548507);16;Platanus;x     1
2.2910717819);16;Corylus;colurna;Betulaceae;;20.0;260.0;Place   1
2.2924448277);16;Paulownia;tomentosa;Paulowniaceae;;20.0;420.0;Place    1
2.29329076205);7;Platanus;orientalis;Platanaceae;1814;20.0;700.0;Quai   1
2.29533455314);7;Maclura;pomifera;Moraceae;1935;13.0;;Quai      1
2.29706549763);7;Eucommia;ulmoides;Eucomiaceae;;12.0;190.0;Quai 1
2.2972574926);15;Alnus;glutinosa;Betulaceae;1933;16.0;220.0;Rue 1
2.30640768208);8;Ginkgo;biloba;Ginkgoaceae;1879;22.0;283.0;Boulevard    1
2.30757576047);8;Platanus;orientalis;Platanaceae;1814;31.0;700.0;Boulevard      1
2.31331809304);8;Calocedrus;decurrens;Cupressaceae;1854;20.0;195.0;Cours-la-Reine,     1
2.31333976248);8;Platanus;orientalis;Platanaceae;1900;20.0;480.0;Cours-la-Reine,       1
2.31595908796);17;Platanus;x    1
2.31951408752);8;Sequoiadendron;giganteum;Taxodiaceae;1850;20.0;320.0;Cours-la-Reine,  1
2.33210374339);9;Pterocarya;fraxinifolia;Juglandaceae;1862;22.0;330.0;Place     1
2.33628540112);14;Sequoia;sempervirens;Taxodiaceae;1935;30.0;335.0;Bd   1
2.3366608746);14;Fagus;sylvatica;Fagaceae;;30.0;370.0;Bd        1
2.33666989768);6;Catalpa;bignonioides;Bignoniaceae;;15.0;260.0;Rue      1
2.33869560229);14;Platanus;x    1
2.34391859224);18;Platanus;orientalis;Platanaceae;1857;27.0;470.0;Place 1
2.34740754195);5;Robinia;pseudoacacia;Fabaceae;1601;11.0;385.0;Quai     1
2.35078878768);13;Aesculus;hippocastanum;Sapindaceae;1894;18.0;355.0;Rue        1
2.35307565328);5;Fagus;sylvatica;Fagaceae;1905;2.0;72.0;Rue     1
2.35399582218);4;Ulmus;carpinifolia;Ulmaceae;1935;15.0;180.0;Place      1
2.3592096955);13;Cedrus;atlantica;Pinaceae;1939;25.0;350.0;128-160      1
2.36062929978);3;Corylus;colurna;Betulaceae;1882;20.0;210.0;Rue 1
2.37007425143);19;Tilia;tomentosa;Malvaceae;1945;20.0;205.0;Place       1
2.37910176561);11;Corylus;colurna;Betulaceae;1879;20.0;245.0;Rue        1
2.38064802989);19;Sequoiadendron;giganteum;Taxodiaceae;;35.0;470.0;Rue  1
2.38129958306);19;Platanus;orientalis;Platanaceae;1862;34.0;670.0;Rue   1
2.38157245444);12;Platanus;x    1
2.38157469859);19;Ginkgo;biloba;Ginkgoaceae;1913;33.0;230.0;Rue 1
2.38367383179);19;Styphnolobium;japonicum;Fabaceae;1873;10.0;335.0;Rue  1
2.39469777758);20;Platanus;x    1
2.39836942721);19;Fraxinus;excelsior;Oleaceae;;30.0;365.0;Boulevard     1
2.39870061217);20;Acer;monspessulanum;Sapindacaees;1833;12.0;225.0;Rue  1
2.39997847741);20;Aesculus;hippocastanum;Sapindaceae;;22.0;345.0;Rue    1
2.40776275516);12;Celtis;australis;Cannabaceae;1906;16.0;295.0;27,      1
2.41033694606);12;Platanus;orientalis;Platanaceae;1860;22.0;475.0;route 1
2.41052012477);12;Platanus;x    1
2.41116455985);12;Platanus;x    1
2.4115101993);12;Diospyros;virginiana;Ebenaceae;1935;12.0;;Ile  1
2.41169855654);12;Taxodium;distichum;Taxodiaceae;1930;20.0;270.0;Ile    1
2.41182825531);12;Taxus;baccata;Taxaceae;1870;5.0;140.0;Ile     1
2.41202933239);12;Liriodendron;tulipifera;Magnoliaceae;1930;22.0;205.0;Ile      1
2.41261756721);12;Juglans;nigra;Juglandaceae;1845;28.0;570.0;route      1
2.41301158121);12;Platanus;x    1
2.41400587444);12;Acer;opalus;Sapindaceae;1870;15.0;160.0;Ile   1
2.42029690936);12;Zelkova;serrata;Ulmaceae;1872;18.0;240.0;;Zelkova     1
2.42111102704);12;Ginkgo;biloba;Ginkgoaceae;1865;25.0;255.0;;Arbre      1
2.43350820893);12;Platanus;x    1
2.43360205128);12;Liriodendron;tulipifera;Magnoliaceae;1862;35.0;305.0;avenue   1
2.43375148978);12;Fagus;sylvatica;Fagaceae;1865;20.0;530.0;avenue       1
2.43381509843);12;Diospyros;virginiana;Ebenaceae;1875;14.0;180.0;avenue 1
2.43791766754);12;Quercus;ilex;Fagaceae;1860;15.0;;route        1
2.43848438671);12;Fagus;sylvatica;Fagaceae;1895;23.0;370.0;Cours        1
2.44524393613);12;Cedrus;libanii;Pinaceae;1829;30.0;440.0;route 1
2.44579219199);12;Pinus;nigra;Pinaceae;1870;25.0;248.0;route    1
2.4497117757);12;Quercus;petraea;Fagaceae;1815;31.0;450.0;;Chêne        1
2.45494779675);12;Zelkova;carpinifolia;Ulmaceae;;12.0;245.0;Route       1
2.45537251962);12;Pinus;bungeana;Pinaceae;;10.0;50.0;Route      1
2.45551492936);12;Pinus;coulteri;Pinaceae;;14.0;225.0;Route     1
2.46016871078);12;Diospyros;kaki;Ebenaceae;;12.0;160.0;Route    1
2.46130493573);12;Quercus;petraea;Fagaceae;1784;30.0;430.0;route        1
2.46422657197);12;Acer;cappadocicum;Sapindaceae;1900;16.0;280.0;avenue  1
27      1
Albert  2
Arènes  1
Arênes, 1
Bagatelle)      1
Bagatelle;Platane       1
Batignolles     1
Belle   1
Benett;Ailanthe;;53;Jardin      1
Benett;Arbre    1
Benett;Chêne    1
Benett;Ptérocarya       1
Benjamin        2
Bercy   1
Bercy)  7
Bercy;Cyprés    1
Bercy;Erable    1
Bercy;If        1
Bercy;Plaqueminier      1
Bercy;Platane   2
Bercy;Tulipier  1
Botzaris;Arbre  1
Botzaris;Platane        1
Botzaris;Sophora        1
Botzaris;Séquoia        1
Boulogne        23
Bourdonnais,    3
Branly, 3
Bretagne,       1
Breuil  4
Butte   1
Buttes  4
Byzance;;15;Square      1
Byzance;;1;Square       1
Byzance;;34;Jardin      1
Canada;;61;Square       1
Cappadoce;;78;Bois      1
Cardinet;Platane        1
Carnot) 4
Cascade)        1
Cascade,        4
Catelan)        4
Catelan;Hêtre   1
Catelan;Kaki;;68;Bois   1
Catelan;Pin     1
Catelan;Séquoia 1
Caucase;;14;Square      1
Caucase;;65;Bois        1
Champs  6
Chapeau 1
Charles 1
Charles-Moureu, 1
Charonne        1
Charonne;Platane        1
Chaumont        4
Chine;;54;Jardin        1
Choisy  1
Choisy, 1
Château 4
Cité‚-Universitaire,    3
Cordelières;Marronnier  1
Corse;;76;Bois  1
Corvisart,      1
Courcelles,     2
Croix   4
Croulebarbe,    1
Daumesnil,      4
Daumesnil/porte 2
Daumesnil;Noyer 1
Daumesnil;Platane       2
Debussy 1
Docteur 1
Docteur-Magn;Cèdre      1
Dorée)  2
Du      1
Ecole   4
Elysées 3
Emile-Deslandres,       1
Esplanade       4
Etienne 1
Eugène-Spuller;Noisetier        1
Ferme,  4
Filion, 1
Foch    3
Foch;Faux       1
Foch;Marronnier 1
Foch;Platane    1
Fontenay)       1
Formig‚,        1
Franklin,       2
Franklin-D.-Roosevelt,  3
François-Truffaut;Platane       1
Gabriel 1
Gabriel;Cèdre   1
Gabriel;Platane 1
Gabriel;Séquoia 1
Gabrielle;Erable        1
Gall    1
Gardette        1
Gazan,  3
Georges-Eastman,        1
Gervais 1
Gervais;Orme    1
Gordon  4
Grande  4
Gravelle)       2
Gravelle,       1
Général-Blaise;Noisetier        1
Général-Guilhem,        1
Inférieur)      1
Inférieur;Cyprés        1
Jacquem;Aulne   1
Japon;;44;Parc  1
Japon;;83;Bois  1
Jean    1
Joseph-Kessel,  1
Jourdan,        3
La      3
Lac     6
Lachaise        2
Lacharrière,    1
Lagrange,       1
Lambert 1
Le      1
Leclerc 1
Liban;;22;Bois  1
Liban;;37;Bois  1
Longchamp)      1
Longchamp,      11
Louise  1
Lutèce  1
L‚on-Lhermitte, 1
Manin,  4
Marigny)        1
Marigny;Hêtre   1
Mars    3
Mar‚chal        1
Matignon,       3
Maurice 2
Maurice);Chêne  1
Mazarine;Catalpa        1
Michel  1
Minimes;Chêne   1
Mirabeau,       1
Monceau 2
Monge;Faux      1
Montebello,     1
Montpellier;;48;Cimetière       1
Montsouris      3
Motte-Piquet,   3
Muette  1
Mun;Noisetier   1
Mun;Paulownia;;35;Jardin        1
Nansouty;Hêtre  1
Nansouty;Platane        1
Nansouty;Séquoia        1
Napoléon;;95;Arboretum  1
Navarre,        1
Neuilly;Arbre   1
Neuilly;Désespoir       1
Neuilly;Hêtre   1
Neuilly;If      1
Neuilly;Platane 2
Neuilly;Séquoia 1
Novembre,       2
Osages;;6;Parc  1
Paul-Albert,    1
Paul-Belmondo,  1
Perinne 1
Perrée, 1
Pierné  1
Point   2
Porte   4
Provence;;16;Avenue     1
Pyramide;Faux   1
Pyramide;Kaki;;58;Jardin        1
Pyramide;Pin    2
Père    2
Reille, 3
René    1
Rochebrune,     1
Rondeaux;Erable 1
Rondeaux;Marronnier     1
Ronsard,        1
Rouge   1
Rue     1
Ruysdael;Arbre  1
Ruysdael;Platane        1
Saint   3
Saint-Julien-le-Pauvre;Robinier 1
Saint-Pierre,   1
Sainte  1
Schumann        1
Seine,  1
Serres  4
Sibérie;;29;Avenue      1
Sibérie;;50;Arboretum   1
Sibérie;;75;Bois        1
Soult   1
Soult;Micocoulier       1
St      1
Stalingrad      1
Stalingrad;Tilleul      1
Suffren;Arbre   1
Suffren;Oranger 1
Suffren;Platane 1
Sèvres  7
Temple  1
Temple, 1
Th‚ophraste-Renaudot,   1
Tourelle,       2
Trocadéro       2
Trocad‚ro       2
Utrillo;Platane 1
Van-Dyck,       2
Versailles;Murier       1
Verzy;Tortuosa;3;Square 1
Vincennes       23
Vincennes;Hêtre 1
Vincennes;Plaqueminier  1
Vincennes;Platane       1
Vincennes;Tulipier      1
Virginie;;81;Bois       1
Virginie;;88;Bois       1
Virginie;;93;Bois       1
Virginie;;94;Bois       1
Viviani 1
Vue;Cèdre       1
Vue;Pin 1
V‚lasquez,      2
acerifolia;Platanaceae;1840;30.0;595.0;Place    1
acerifolia;Platanaceae;1840;40.0;580.0;Bd       1
acerifolia;Platanaceae;1847;40.0;480.0;Allée    1
acerifolia;Platanaceae;1852;30.0;525.0;Avenue   1
acerifolia;Platanaceae;1860;42.0;405.0;Ile      1
acerifolia;Platanaceae;1860;45.0;405.0;Ile      1
acerifolia;Platanaceae;1871;25.0;490.0;route    1
acerifolia;Platanaceae;1872;40.0;520.0;Route    1
acerifolia;Platanaceae;1880;20.0;395.0;148      1
acerifolia;Platanaceae;1918;32.0;570.0;avenue   1
acerifolia;Platanaceae;;35.0;510.0;Rue  1
argenté;;43;Place       1
aux     7
avenue  39
bataille        1
bleu    2
boulevard       4
carrefour       8
cascade)        2
cascades;Cyprés 1
cascades;Cèdre  1
cascades;Magnolia       1
cascades;Pin    1
ceinture        3
champêtre;;2;Place      1
chauve;;56;Bois 1
chauve;;77;Bois 1
chauve;;87;Bois 1
chiens  2
commun;;17;Parc 1
commun;;21;Bois 1
commun;;26;Parc 1
commun;;36;Bois 1
commun;;40;Bois 1
commun;;41;Square       1
commun;;51;Alignement   1
commun;;52;Square       1
commun;;55;Avenue       1
commun;;5;Square        1
commun;;74;Bois 1
commun;;82;Bois 1
commun;;89;Bois 1
commun;;90;Bois 1
commun;;92;Bois 1
cônes;;96;Arboretum     1
d'Algérie;Frêne 1
d'Auteuil       4
d'Auteuil,      4
d'Estienne-d'Orves;Pérocarya    1
d'Inde;;23;Square       1
d'Inde;;30;Avenue       1
d'Inde;;47;Cimetière    1
d'Italie;;91;Bois       1
d'Orient;;13;Jardin     1
d'Orient;;42;Square     1
d'Orient;;45;Parc       1
d'Orient;;49;Bois       1
d'Orient;;73;Bois       1
d'Orient;;86;Bois       1
d'Orient;;8;Parc        1
d'Orient;;9;Parc        1
d'Orves 1
d'aveugle)      2
daumesnil)      1
de      172
des     24
du      51
encens;;11;Jardin       1
et      2
faux-acacia;;4;Square   1
fleurs;;66;Bois 1
glutineux;;28;Square    1
grande  1
grandes 1
grands  1
gravelle)       1
guide   2
gutta-percha;;7;Parc    1
géant;;12;Jardin        1
géant;;57;Parc  1
géant;;59;Bois  1
géant;;67;Bois  1
géant;;72;Bois  1
inférieur)      5
inférieur;Platane       1
james)  1
l'      1
l'Ambroise,     1
l'Atlas 1
l'Atlas;Glauca;24;Parc  1
la      36
lac     7
laricio;Pinaceae;1882;30.0;240.0;All‚e  1
liège;;32;Jardin        1
minimes)        1
neuf)   1
noir;;69;Bois   1
noir;;85;Bois   1
noir;Austriaca;97;Bois  1
orme    3
papier;;33;Parc 1
pendula;62;Square       1
ple;Glauca      1
pleureur;Pendula;20;Bois        1
pleureur;Pendula;63;Bois        1
pleureur;Pendula;70;Bois        1
pochettes;;71;Bois      1
pourpre;Purpurea;18;Bois        1
pourpre;Purpurea;25;Parc        1
pourpre;Purpurea;38;Bois        1
pourpre;Purpurea;60;Stade       1
quarante        5
repos,  2
ronde   1
route   14
rouve;;80;Bois  1
rouvre;;19;Bois 1
rue     43
sempervirent;;27;Parc   1
singe;;39;Bois  1
vert;;98;Bois   1
à       13
écus;;10;Parc   1
écus;;31;Jardin 1
écus;;46;Parc   1
écus;;64;Bois   1
écus;;84;Bois   1
île     1
```
*Write a MapReduce job that displays the list of distinct containing trees in this
file:

 [j.crecel@hadoop-edge01 ~]$ nano trees_mapreduce.java

```sh
public class trees_Mapper extends Mapper<Object, Text, Text, IntWritable> {
	public int curr_line = 0;
	public void map(Object key, Text value, Context context) throws IOException, InterruptedException {
		if (curr_line != 0) {
			context.write(new Text(value.toString().split(";")[1]), new IntWritable(1));
		}
		curr_line++;
	}
}

public class  trees_Reducer extends Reducer<Text, IntWritable, Text, IntWritable> {
    public void reduce(Text key, Iterable<IntWritable> values, Context context)
            throws IOException, InterruptedException {
    	int sum = 0;
        for (IntWritable val : values) {
            sum += val.get();
        }
    	context.write(key, new IntWritable(sum));
    }
}
```

- 1.8.2 Show all existing species 

 [j.crecel@hadoop-edge01 ~]$ nano species_mapreduce.java
```sh
public class species_Mapper extends Mapper<Object, Text, Text, NullWritable> {
	public int curr_line = 0;

	public void map(Object key, Text value, Context context) throws IOException, InterruptedException {
		if (curr_line != 0) {
			context.write(new Text(value.toString().split(";")[3]), NullWritable.get());
		}
		curr_line++;
	}
}

public class species_Reducer extends Reducer<Text, IntWritable, Text, NullWritable> {
	public void reduce(Text key, Iterable<IntWritable> values, Context context)
			throws IOException, InterruptedException {
		context.write(key, NullWritable.get());
	}
}
```

-  1.8.3 Number of trees by kinds 

 [j.crecel@hadoop-edge01 ~]$ nano Number_mapreduce.java
```sh
public class Number_Mapper extends Mapper<Object, Text, Text, IntWritable> {
	public int curr_line = 0;

	public void map(Object key, Text value, Context context) throws IOException, InterruptedException {
		if (curr_line != 0) {
			context.write(new Text(value.toString().split(";")[3]), new IntWritable(1));
		}
		curr_line++;
	}
}

public class Number_Reducer extends Reducer<Text, IntWritable, Text, IntWritable> {
	public void reduce(Text key, Iterable<IntWritable> values, Context context)
			throws IOException, InterruptedException {
		int sum = 0;
		for (IntWritable val : values) {
			sum += val.get();
		}
		context.write(key, new IntWritable(sum));
	}
}
```

- 1.8.4 Maximum height per kind of tree  

 [j.crecel@hadoop-edge01 ~]$ nano Maximum_height_mapreduce.java
```sh
public class Maximum_height_Mapper extends Mapper<Object, Text, Text, FloatWritable> {
	public int curr_line = 0;

	public void map(Object key, Text value, Context context) throws IOException, InterruptedException {
		if (curr_line != 0) {
			try {
				Float height = Float.parseFloat(value.toString().split(";")[6]);
				context.write(new Text(value.toString().split(";")[3]), new FloatWritable(height));
			} catch (NumberFormatException ex) {
				// If the value is not a float, skip it by catching the error from the parseFloat() method
			}
		} curr_line++;
	}
}

public class Maximum_height_Reducer extends Reducer<Text, FloatWritable, Text, FloatWritable> {
    public class HeightSpeciesReducer extends Reducer<Text, FloatWritable, Text, FloatWritable> {
    	public void reduce(Text key, Iterable<FloatWritable> values, Context context)
    			throws IOException, InterruptedException {
    		context.write(key, new FloatWritable(StreamSupport.stream(values.spliterator(), false)
    				.map((v) -> { return v.get(); }).
    				max(Float::compare).get()));
    	}
    }

}
```

- 1.8.5 Sort the trees height from smallest to largest (average)
 [j.crecel@hadoop-edge01 ~]$ nano sort_mapreduce.java
```sh
public sort_Mapper extends Mapper<Object, Text, FloatWritable, Text> {
	public int curr_line = 0;

	public void map(Object key, Text value, Context context) throws IOException, InterruptedException {
		if (curr_line != 0) {
			try {
				String[] line_tokens = value.toString().split(";");
				Float height = Float.parseFloat(line_tokens[6]);
				context.write(new FloatWritable(height),
						new Text(line_tokens[11] + " - " + line_tokens[2] + " " + line_tokens[3] + " (" + line_tokens[4] + ")"));
			} catch (NumberFormatException ex) {
				// If the value is not a float, skip by catching the error from the parseFloat() method
			}
		} curr_line++;
	}
}

public class sort_Reducer extends Reducer<FloatWritable, Text, Text, FloatWritable> {
	public void reduce(FloatWritable key, Iterable<Text> values, Context context)
			throws IOException, InterruptedException {
		for (Text val : values) {
			context.write(val, key);
		}
	}
}
```

-  1.8.6 District containing the oldest tree (difficult)
 [j.crecel@hadoop-edge01 ~]$ nano oldest_mapreduce.java
```sh
public class oldest_Mapper extends Mapper<Object, Text, IntWritable, IntWritable> {
	public int curr_line = 0;

	public void map(Object key, Text value, Context context) throws IOException, InterruptedException {
		if (curr_line != 0) {
			try {
				Integer year = Integer.parseInt(value.toString().split(";")[5]);
				context.write(new IntWritable(year), new IntWritable(Integer.parseInt(value.toString().split(";")[1])));
			} catch (NumberFormatException ex) {
				// If the year is not an integer, skip by catching the error from the parseFloat() method
			}
		} curr_line++;
	}
}

public class oldest_reducer extends Reducer<IntWritable, IntWritable, IntWritable, IntWritable> {
	public boolean first = true;

	public void reduce(IntWritable key, Iterable<IntWritable> values, Context context)
			throws IOException, InterruptedException {
		if (first) {
			StreamSupport.stream(values.spliterator(), false).distinct().forEach(v -> {
				try {
					context.write(key, v);
				} catch (IOException | InterruptedException e) {
					e.printStackTrace();
				}
			});
		}
		first = false;
	}
}
```

- 1.8.7 District containing the most trees (very difficult)
	 [j.crecel@hadoop-edge01 ~]$ nano Most_mapreduce.java
```sh
public class Most_Mapper extends Mapper<LongWritable, IntWritable, NullWritable, MapWritable> {
	public void map(LongWritable key, IntWritable value, Context context) throws IOException, InterruptedException {
		MapWritable map = new MapWritable();
		map.put(new IntWritable((int) key.get()), value);
		context.write(NullWritable.get(), map);
	}
}

public class Most_Reducer extends Reducer<NullWritable, MapWritable, IntWritable, IntWritable> {
    public void reduce(NullWritable key, Iterable<MapWritable> values, Context context)
            throws IOException, InterruptedException {
		ArrayList<Integer[]> district_trees = (ArrayList<Integer[]>) StreamSupport.stream(values.spliterator(), false)
				.map( mw ->  (new Integer[] { ((IntWritable) mw.keySet().toArray()[0]).get(), ((IntWritable) mw.get(mw.keySet().toArray()[0])).get() }))
				.collect(Collectors.toList());
		// Copies the iterable to an arraylist so multiple operations can be done on the iterable

		int max_trees = district_trees.stream().map((arr) -> arr[1]).max(Integer::compare).get();

		district_trees.stream().filter(arr -> arr[1] == max_trees).map(arr -> arr[0]).distinct().forEach((district) -> { try {
			context.write(new IntWritable(max_trees), new IntWritable(district));
		} catch (IOException | InterruptedException e) {
			e.printStackTrace();
		} });
    }
}
```

