cmake_minimum_required(VERSION 3.5.1)
project("pyvxl-contrib-bpgl-algo")

# Add pybind11 module
pybind11_add_module(pybpgl_algo pybpgl_algo.h pybpgl_algo.cxx)

# Link to vxl library
target_link_libraries(pybpgl_algo PRIVATE bpgl_algo)

# Set names
set_target_properties(pybpgl_algo PROPERTIES OUTPUT_NAME "_bpgl_algo")

# install the .so file to the python install dir
install(TARGETS pybpgl_algo DESTINATION ${PYTHON_SITE}/vxl/contrib/bpgl/algo)

# auto generate __init__ file
install(CODE "file(WRITE ${PYTHON_SITE}/vxl/contrib/bpgl/algo/__init__.py \"from ._bpgl_algo import *\")")

