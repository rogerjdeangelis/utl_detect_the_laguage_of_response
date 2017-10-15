# utl_detect_the_laguage_of_response
Given a comment, detect the language. Is the text one of 74 languages.

    ```  Detecting t=the languge used in a comment (IML/R WPS Proc-R)                                                                                                 ```
    ```                                                                                                                                                               ```
    ```                                                                                                                                                               ```
    ```    WORKING CODE                                                                                                                                               ```
    ```    WPS Proc R/ IML/R (probably Pyhthon can also do this)                                                                                                      ```
    ```                                                                                                                                                               ```
    ```     INPUT                                                                                                                                                     ```
    ```       This is an English sentence.                                                                                                                            ```
    ```       Das ist ein deutscher Satz.                                                                                                                             ```
    ```       Esta es una frase en espa~nol.                                                                                                                          ```
    ```                                                                                                                                                               ```
    ```     CODE                                                                                                                                                      ```
    ```       want<-textcat(have$TXT);                                                                                                                                ```
    ```                                                                                                                                                               ```
    ```     OUTPUT                                                                                                                                                    ```
    ```       WORK.WANTWPS total obs=3                                                                                                                                ```
    ```                                                                                                                                                               ```
    ```       Obs     WANT                                                                                                                                            ```
    ```        1     english                                                                                                                                          ```
    ```        2     german                                                                                                                                           ```
    ```        3     spanish                                                                                                                                          ```
    ```                                                                                                                                                               ```
    ```                                                                                                                                                               ```
    ```  see                                                                                                                                                          ```
    ```  https://goo.gl/dzfqgb                                                                                                                                        ```
    ```  https://communities.sas.com/t5/SAS-Text-and-Content-Analytics/Detecting-English-comments-from-a-corpus-of-customer-complaints/m-p/400656                     ```
    ```                                                                                                                                                               ```
    ```  Bens solution ( there are other intersesting solutions)                                                                                                      ```
    ```  https://stackoverflow.com/questions/8078604/detect-text-language-in-r                                                                                        ```
    ```                                                                                                                                                               ```
    ```  Ben profile                                                                                                                                                  ```
    ```  https://stackoverflow.com/users/1036500/ben                                                                                                                  ```
    ```                                                                                                                                                               ```
    ```                                                                                                                                                               ```
    ```  HAVE                                                                                                                                                         ```
    ```  ====                                                                                                                                                         ```
    ```                                                                                                                                                               ```
    ```    SD1.HAVE total obs=3                                                                                                                                       ```
    ```                                                                                                                                                               ```
    ```    Obs                 TXT                                                                                                                                    ```
    ```                                                                                                                                                               ```
    ```     1     This is an English sentence.                                                                                                                        ```
    ```     2     Das ist ein deutscher Satz.                                                                                                                         ```
    ```     3     Esta es una frase en espa~nol.                                                                                                                      ```
    ```                                                                                                                                                               ```
    ```  WANT                                                                                                                                                         ```
    ```  ====                                                                                                                                                         ```
    ```    WORK.WANTWPS                                                                                                                                               ```
    ```  total obs=3                                                                                                                                                  ```
    ```                                                                                                                                                               ```
    ```    Obs     WANT                                                                                                                                               ```
    ```                                                                                                                                                               ```
    ```     1     english                                                                                                                                             ```
    ```     2     german                                                                                                                                              ```
    ```     3     spanish                                                                                                                                             ```
    ```                                                                                                                                                               ```
    ```  *                _               _       _                                                                                                                   ```
    ```   _ __ ___   __ _| | _____     __| | __ _| |_ __ _                                                                                                            ```
    ```  | '_ ` _ \ / _` | |/ / _ \   / _` |/ _` | __/ _` |                                                                                                           ```
    ```  | | | | | | (_| |   <  __/  | (_| | (_| | || (_| |                                                                                                           ```
    ```  |_| |_| |_|\__,_|_|\_\___|   \__,_|\__,_|\__\__,_|                                                                                                           ```
    ```                                                                                                                                                               ```
    ```  ;                                                                                                                                                            ```
    ```                                                                                                                                                               ```
    ```  options validvarname=upcase;                                                                                                                                 ```
    ```  libname sd1 "d:/sd1";                                                                                                                                        ```
    ```  data sd1.have;                                                                                                                                               ```
    ```   length txt $96;                                                                                                                                             ```
    ```   input;                                                                                                                                                      ```
    ```   txt=_infile_;                                                                                                                                               ```
    ```  cards4;                                                                                                                                                      ```
    ```  This is an English sentence.                                                                                                                                 ```
    ```  Das ist ein deutscher Satz.                                                                                                                                  ```
    ```  Esta es una frase en espa~nol.                                                                                                                               ```
    ```  ;;;;                                                                                                                                                         ```
    ```  run;quit;                                                                                                                                                    ```
    ```                                                                                                                                                               ```
    ```                                                                                                                                                               ```
    ```  *          _       _   _                                                                                                                                     ```
    ```   ___  ___ | |_   _| |_(_) ___  _ __                                                                                                                          ```
    ```  / __|/ _ \| | | | | __| |/ _ \| '_ \                                                                                                                         ```
    ```  \__ \ (_) | | |_| | |_| | (_) | | | |                                                                                                                        ```
    ```  |___/\___/|_|\__,_|\__|_|\___/|_| |_|                                                                                                                        ```
    ```                                                                                                                                                               ```
    ```  ;                                                                                                                                                            ```
    ```                                                                                                                                                               ```
    ```  %utl_submit_wps64('                                                                                                                                          ```
    ```  libname sd1 "d:/sd1";                                                                                                                                        ```
    ```  options set=R_HOME "C:/Program Files/R/R-3.4.0";                                                                                                             ```
    ```  libname wrk "%sysfunc(pathname(work))";                                                                                                                      ```
    ```  proc r;                                                                                                                                                      ```
    ```  submit;                                                                                                                                                      ```
    ```  source("C:/Program Files/R/R-3.4.0/etc/Rprofile.site", echo=T);                                                                                              ```
    ```  library(haven);                                                                                                                                              ```
    ```  library(textcat);                                                                                                                                            ```
    ```  have<-read_sas("d:/sd1/have.sas7bdat");                                                                                                                      ```
    ```  want<-textcat(have$TXT);                                                                                                                                     ```
    ```  endsubmit;                                                                                                                                                   ```
    ```  import r=want data=wrk.wantwps;                                                                                                                              ```
    ```  run;quit;                                                                                                                                                    ```
    ```  ');                                                                                                                                                          ```
    ```
