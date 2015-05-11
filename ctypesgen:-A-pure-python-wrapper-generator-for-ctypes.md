This project automatically generates ctypes wrappers for header files written in C.

For example, if you'd like to generate Neon bindings, you can do so using this recipe:
{{{
  $ python ctypesgen.py -lneon /usr/local/include/neon/ne_*.h -o neon.py
}}}
Some libraries, such as APR, need special flags to compile. You can pass these flags in on the command line.

For example:
{{{
 $ FLAGS = `apr-1-config --cppflags --includes`
 $ python ctypesgen.py $FLAGS -llibapr-1.so $HOME/include/apr-1/apr*.h -o apr.py
}}}

Sometimes, libraries will depend on each other. You can specify these dependencies using -mmodule, where module is the name of the dependency module. Here's an example for apr_util:

{{{
 $ python ctypesgen.py $FLAGS -llibaprutil-1.so $HOME/include/apr-1/ap[ru]*.h -mapr -o apr_util.py
}}}