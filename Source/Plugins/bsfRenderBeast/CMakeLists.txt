# Source files and their filters
include(CMakeSources.cmake)
	
# Target
add_library(bsfRenderBeast SHARED ${BS_RENDERBEAST_SRC})

# Common flags
add_common_flags(bsfRenderBeast)

# Includes
target_include_directories(bsfRenderBeast PRIVATE "./")

# Defines
target_compile_definitions(bsfRenderBeast PRIVATE -DBS_BSRND_EXPORTS)

# Libraries
## Local libs
target_link_libraries(bsfRenderBeast bsf)

# IDE specific
set_property(TARGET bsfRenderBeast PROPERTY FOLDER Plugins)

# Install
if(RENDERER_MODULE MATCHES "RenderBeast")
	install_bsf_target(bsfRenderBeast)
endif()

conditional_cotire(bsfRenderBeast)
