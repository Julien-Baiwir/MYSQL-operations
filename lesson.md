mets tout ce texte en markdown :mets le titre avec ## ,si il y a du langage sql mets le language SQL en markdown  entre ```    ```  et si il y a un tableau mets le tableau en markdown également:


SQL Lesson 12: Order of execution of a Query

SELECT DISTINCT column, AGG_FUNC(column_or_expression), …
FROM mytable
    JOIN another_table
      ON mytable.column = another_table.column
    WHERE constraint_expression
    GROUP BY column
    HAVING constraint_expression
    ORDER BY column ASC/DESC
    LIMIT count OFFSET COUNT;




