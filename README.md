# utl-macro-lists-like-automatic-user-to-ods-destinations

Macro lists like automatic user to ods destinations.  Keywords: sas sql join merge big data analytics macros oracle teradata mysql sas communities stackoverflow statistics artificial inteligence AI Python R Java Javascript WPS Matlab SPSS Scala Perl C C# Excel MS Access JSON graphics maps NLP natural language processing machine learning igraph DOSUBL DOW loop stackoverflow SAS community.

    Macro lists like automatic and user to ods destinations

    github
    https://tinyurl.com/ycslhjrf
    https://github.com/rogerjdeangelis/utl-macro-lists-like-automatic-user-to-ods-destinations

    see SAS doc
    http://support.sas.com/documentation/cdl/en/mcrolref/62978/HTML/default/viewer.htm#n189qvy83pmkt6n1bq2mmwtyb4oe.htm

    _ALL_       lists the values of all user-generated and automatic macro variables.
    _AUTOMATIC_ lists the values of automatic macro variables.
    _GLOBAL_    lists user-generated global macro variables. The scope is identified as GLOBAL.
    _LOCAL_     lists user-generated local macro variables. The scope is the name of the currently executing macro.
    _USER_      lists user-generated global and local macro variables.

    github macros
    https://tinyurl.com/y9nfugth
    https://github.com/rogerjdeangelis/utl-macros-used-in-many-of-rogerjdeangelis-repositories


    INPUT
    =====

     %utl_usrdelmac;          * delete all _user_ macro variablel;

     %array(num_,values=0-5); * create macro variables nums_;

     %put _user_;

     GLOBAL NUM_1 0
     GLOBAL NUM_2 1
     GLOBAL NUM_3 2
     GLOBAL NUM_4 3
     GLOBAL NUM_5 4
     GLOBAL NUM_6 5

     GLOBAL NUM_N 6  /* number in array */


     %put _USER_     ;

     * can also put these lists into an rtf file;

     %put _ALL_      ;
     %put _AUTOMATIC_;
     %put _GLOBAL_   ;
     %put _LOCAL_    ;


    EXAMPLE OUTPUT (rtf file)
    =========================

       d:/rtf/putuser.rtf

         GLOBAL NUM_1 0
         GLOBAL NUM_2 1
         GLOBAL NUM_3 2
         GLOBAL NUM_4 3
         GLOBAL NUM_5 4
         GLOBAL NUM_6 5

         GLOBAL NUM_N 6


    PROCESS
    =======

    %utl_usrdelmac;           * delete all _user_ macro variablel;

    %array(num_,values=0-5);  * create new user macro variables and values;

    ods rtf body="d:/rtf/putuser.rtf";

    data _null_;

      if _n_=0 then do;
         %let rc=%sysfunc(dosubl('

            %utlnopts;  /* important - minimize log to just the puts */;
            run;quit;

            %symdel rc; * delete rc macro variable created by utlnopts;

            proc printto log="%sysfunc(pathname(work))/log.txt" new;
            run;quit;

            %put _user_;
            run;quit;

            proc printto;
            run;quit;

            %utlopts; /* turn options on;
            '));
      end;

      infile "%sysfunc(pathname(work))/log.txt";
      input;

      macval=_infile_;
      file print ods;
      put _ods_;

    run;quit;

    ods rtf close;

    *                _               _       _
     _ __ ___   __ _| | _____     __| | __ _| |_ __ _
    | '_ ` _ \ / _` | |/ / _ \   / _` |/ _` | __/ _` |
    | | | | | | (_| |   <  __/  | (_| | (_| | || (_| |
    |_| |_| |_|\__,_|_|\_\___|   \__,_|\__,_|\__\__,_|

    ;

    %utl_usrdelmac;           * delete all _user_ macro variablel;

    %array(num_,values=0-5);  * create new user macro variables and values;


