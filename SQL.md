**Change case of table's name**

``` sql
# call toggleCase('leagueofnerds',1); To upper case
# call toggleCase('leagueofnerds',0); To lower case
    
    DELIMITER $$
    DROP PROCEDURE IF EXISTS `toggleCase` $$
    
    CREATE PROCEDURE `toggleCase` (in_db varchar(20),in_add_rem TINYINT(1))
      BEGIN
    
        DECLARE done INT default 0;
        DECLARE tbl_nm VARCHAR(30);
        DECLARE ren VARCHAR(200);
    
        DECLARE table_cur CURSOR FOR select table_name from information_schema.tables where table_schema=in_db;
    
        DECLARE CONTINUE HANDLER FOR NOT FOUND SET done=1;
        OPEN table_cur;
        rename_loop:LOOP
          FETCH table_cur INTO tbl_nm;
          IF done=1 THEN
            LEAVE rename_loop;
          END IF;
          if in_add_rem=1 then #ADD
            SET @ren = concat("rename table ", in_db,'.',tbl_nm ," to ",in_db,'.',UCASE(tbl_nm),";");
            SELECT concat("UP: ",tbl_nm, " => ", UCASE(tbl_nm));
          else
            SET @ren = concat("rename table ", in_db,'.',tbl_nm ," to ",in_db,'.',LCASE(tbl_nm),";");
            SELECT concat("LOW: ",tbl_nm, " => ", LCASE(tbl_nm));
          end if;
          prepare ren from @ren;
          execute ren;
        END LOOP;
    
        CLOSE table_cur;
        select table_name 'Tables' from information_schema.tables where table_schema=in_db;
    
      END $$
    
    DELIMITER;
```
