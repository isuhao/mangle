GCC=g++ -I../ -Wall -Werror

all: memory_server_test buffer_filter_test file_server_test slice_filter_test file_write_test iostream_test cap_test buffer_writer_test copy_test string_stream_test

# CURRENTLY DISABLED for dependency reasons (the examples should be OK)
# ogre_client_test audiere_client_test

I_OGRE=$(shell pkg-config --cflags OGRE)
L_OGRE=$(shell pkg-config --libs OGRE)
L_AUDIERE=-laudiere

ogre_client_test: ogre_client_test.cpp ../stream.hpp ../clients/ogre_datastream.hpp
	$(GCC) $< -o $@ $(I_OGRE) $(L_OGRE)

audiere_client_test: audiere_client_test.cpp ../stream.hpp ../clients/audiere_file.hpp ../clients/audiere_file.cpp
	$(GCC) $< -o $@ ../clients/audiere_file.cpp $(L_AUDIERE)

iostream_test: iostream_test.cpp ../clients/io_stream.cpp
	$(GCC) $^ -o $@

file_server_test: file_server_test.cpp ../stream.hpp ../servers/file_stream.hpp ../servers/std_stream.hpp
	$(GCC) $< -o $@

file_write_test: file_write_test.cpp ../stream.hpp ../servers/outfile_stream.hpp ../servers/std_ostream.hpp
	$(GCC) $< -o $@

memory_server_test: memory_server_test.cpp ../stream.hpp ../servers/memory_stream.hpp
	$(GCC) $< -o $@

string_stream_test: string_stream_test.cpp ../stream.hpp ../servers/memory_stream.hpp ../servers/string_stream.hpp
	$(GCC) $< -o $@

buffer_filter_test: buffer_filter_test.cpp ../stream.hpp ../servers/memory_stream.hpp ../filters/buffer_stream.hpp
	$(GCC) $< -o $@

buffer_writer_test: buffer_writer_test.cpp ../stream.hpp ../servers/memory_stream.hpp ../servers/buffer_writer.hpp
	$(GCC) $< -o $@

slice_filter_test: slice_filter_test.cpp ../stream.hpp ../servers/memory_stream.hpp ../filters/slice_stream.hpp
	$(GCC) $< -o $@

cap_test: cap_test.cpp ../stream.hpp ../servers/memory_stream.hpp ../filters/cap_stream.hpp
	$(GCC) $< -o $@

copy_test: copy_test.cpp ../stream.hpp ../servers/memory_stream.hpp ../clients/copy_stream.hpp ../servers/string_writer.hpp
	$(GCC) $< -o $@

clean:
	rm *_test
