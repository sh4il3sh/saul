    "OLD SYNTAX
    DATA lo_tabledescr TYPE REF TO cl_abap_tabledescr.
    DATA lo_structdescr TYPE REF TO cl_abap_structdescr.
    DATA input TYPE string.

    lo_tabledescr ?= cl_abap_tabledescr=>describe_by_data( <lt_tabinput> ).
    lo_structdescr ?= lo_tabledescr->get_table_line_type( ).

    LOOP AT lo_structdescr->components ASSIGNING FIELD-SYMBOL(<fs_comp>).
      input = input && cl_abap_char_utilities=>horizontal_tab && <fs_comp>-name.
    ENDLOOP.
    SHIFT input LEFT.

    "NEW SYNTAX
    ls_input =
    REDUCE #( INIT tabinput = ` `
              FOR <ls_component> IN
               CAST cl_abap_structdescr(
                 CAST cl_abap_tabledescr(
                  cl_abap_tabledescr=>describe_by_data( <lt_tabinput> ) )->get_table_line_type( ) )->components
              INDEX INTO index
              NEXT tabinput &&= COND #( WHEN index > 1 THEN cl_abap_char_utilities=>horizontal_tab ) && <ls_component>-name
                  ).
