OCAMLC=ocamlfind ocamlc -g -thread -package session-ocaml,session-ocaml.ppx -rectypes -short-paths
OCAMLOPT=ocamlfind ocamlopt -thread -package session-ocaml,session-ocaml.ppx -rectypes -short-paths
OCAMLMKTOP=ocamlfind ocamlmktop -thread -package session-ocaml -rectypes
OCAMLDEP=ocamlfind ocamldep -package session-ocaml

EXAMPLES=smtp2 example_journal1 example_journal2 example_journal3

EXAMPLES_BYTE = $(EXAMPLES:%=%.byte)
EXAMPLES_NATIVE = $(EXAMPLES:%=%.native)


all: $(EXAMPLES_BYTE) $(EXAMPLES_NATIVE)

# Common rules
.SUFFIXES: .ml .mli .cmo .cmi .cmx .byte .native

example_journal3.byte: example_journal2.cmo example_journal3.cmo
	$(OCAMLC) -package session-ocaml.net -linkpkg -o $@ $^

example_journal3.native: example_journal2.cmx example_journal3.cmx
	$(OCAMLOPT) -package session-ocaml.net -linkpkg -o $@ $^

example_journal3.cmo: example_journal2.cmo

example_journal3.cmx: example_journal2.cmx

.cmo.byte:
	$(OCAMLC) -package session-ocaml.net -linkpkg -o $@ $^

.cmx.native:
	$(OCAMLOPT) -package session-ocaml.net -linkpkg -o $@ $^

.ml.cmo:
	$(OCAMLC) -c $<

.ml.cmx:
	$(OCAMLOPT) -c $< 

# Clean up
clean:
	rm -f *.top *.native *.byte
	rm -f *.cm[ioaxt] *.cmax *.cmti *.o *.annot

# Dependencies
depend:
	$(OCAMLDEP) $(INCLUDES) *.mli *.ml > .depend

include .depend
