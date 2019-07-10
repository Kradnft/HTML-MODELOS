

dadof('richard','santiago').
dadof('richard','alejandro').
dadof('angela','santiago').
dadof('angela','alejandro').


dadof('segundo','richard').
dadof('idalid','richard').
dadof('vidal','angela').
dadof('amadis','angela').

dadof('manuel','segundo').
dadof('dinora','amadis').


dadof('segundo','aby').
dadof('segundo','alex').
dadof('segundo','mei').
dadof('segundo','omar').

dadof('amadis','victor').
dadof('amadis','gildardo').

dadof('aby','jenny').
dadof('aby','camilo').

dadof('luis','jenny').
dadof('luis','camilo').

dadof('alex','samuel').
dadof('alex','aleja').
dadof('alex','ximena').
dadof('max','samuel').
dadof('max','ximena').
dadof('max','aleja').


dadof('omar','mario').
dadof('omar','sofia').
dadof('maria','mario').
dadof('maria','sofia').

dadof('mei','cata').
dadof('mei','david').
dadof('laura','cata').
dadof('laura','david').


sonof(X,Y) :- dadof(Y,X).

grandpaof(X,Y) :- dadof(X,Z), dadof(Z,Y).

grandsonof(X,Y) :-  grandpaof(Y,X).

brotherof(X,Y) :- dadof(Z,X), dadof(Z,Y), X \== Y.

bisgrandpaof(X,Y) :- grandpaof(X,Z), dadof(Z,Y).

bisgrandsonof(X,Y) :- bisgrandpaof(Y,X).

uncleof(X,Y) :-  brotherof(X,Z), dadof(Z,Y).

nephewof(X,Y) :-  uncleof(Y,X).

cousinof(X,Y) :-  uncleof(X,Z), dadof(Z,Y).

marriedwith(X,Y) :- dadof(X,Z), dadof(Y,Z), X \== Y.

behappy(X) :-  marriedwith(X,Z).
