set(PROJECT_NAME libultraship)

if (CMAKE_SYSTEM_NAME STREQUAL "Darwin")
    enable_language(OBJCXX)
    #set(CMAKE_OBJCXX_FLAGS "-Wno-deprecated-declarations -ObjC++")
endif()

################################################################################
# Source groups
################################################################################
set(Header_Files__Resources__Factories
    "Factories/AnimationFactory.h"
    "Factories/ArrayFactory.h"
    "Factories/AudioFactory.h"
    "Factories/BlobFactory.h"
    "Factories/CollisionHeaderFactory.h"
    "Factories/CutsceneFactory.h"
    "Factories/DisplayListFactory.h"
    "Factories/MaterialFactory.h"
    "Factories/MtxFactory.h"
    "Factories/PathFactory.h"
    "Factories/PlayerAnimationFactory.h"
    "Factories/ResourceLoader.h"
    "Factories/SceneFactory.h"
    "Factories/SkeletonFactory.h"
    "Factories/SkeletonLimbFactory.h"
    "Factories/TextFactory.h"
    "Factories/TextureFactory.h"
    "Factories/VtxFactory.h"
)
source_group("Header Files\\Resources\\Factories" FILES ${Header_Files__Resources__Factories})

set(Header_Files__Resources__Files
    "Animation.h"
    "Array.h"
    "Audio.h"
    "Blob.h"
    "CollisionHeader.h"
    "Cutscene.h"
    "DisplayList.h"
    "Material.h"
    "Matrix.h"
    "Model.h"
    "Path.h"
    "PlayerAnimation.h"
    "Scene.h"
    "Skeleton.h"
    "SkeletonLimb.h"
    "Text.h"
    "Texture.h"
    "Vertex.h"
)
source_group("Header Files\\Resources\\Files" FILES ${Header_Files__Resources__Files})

set(Source_Files__Audio
    "abi.h"
    "AudioPlayer.h"
    "mixer.c"
    "mixer.h"
    "SDLAudioPlayer.cpp"
    "SDLAudioPlayer.h"
)

if (CMAKE_SYSTEM_NAME STREQUAL "Windows")
set(Source_Files__Audio__extra
    "WasapiAudioPlayer.cpp"
    "WasapiAudioPlayer.h"
)
else()
set(Source_Files__Audio__extra
    "PulseAudioPlayer.cpp"
    "PulseAudioPlayer.h"
)
endif ()

source_group("Source Files\\Audio" FILES ${Source_Files__Audio} ${Source_Files__Audio__extra})

set(Source_Files__Controller
    "ControlDeck.cpp"
    "ControlDeck.h"
    "Controller.cpp"
    "Controller.h"
    "ControllerAttachment.cpp"
    "ControllerAttachment.h"
    "InputEditor.cpp"
    "InputEditor.h"
    "KeyboardController.cpp"
    "KeyboardController.h"
    "SDLController.cpp"
    "SDLController.h"
    "UltraController.h"
    "VirtualController.h"
)
source_group("Source Files\\Controller" FILES ${Source_Files__Controller})

set(Source_Files__Controller__Attachment
    "ControllerAttachment.cpp"
    "ControllerAttachment.h"
    "MemoryPack.cpp"
    "MemoryPack.h"
    "RumblePack.cpp"
    "RumblePack.h"
)
source_group("Source Files\\Controller\\Attachment" FILES ${Source_Files__Controller__Attachment})

set(Source_Files__CustomImpl
    "GameOverlay.cpp"
    "GameOverlay.h"
    "Console.cpp"
    "Console.h"
    "ImGuiImpl.cpp"
    "ImGuiImpl.h"
)
source_group("Source Files\\CustomImpl" FILES ${Source_Files__CustomImpl})

set(Source_Files__CustomImpl__Hooks
    "Hooks.h"
)
source_group("Source Files\\CustomImpl\\Hooks" FILES ${Source_Files__CustomImpl__Hooks})

set(Source_Files__CustomImpl__Utils
    "Utils.cpp"
    "Utils.h"
)
source_group("Source Files\\CustomImpl\\Utils" FILES ${Source_Files__CustomImpl__Utils})

set(Source_Files__Globals
    "Cvar.cpp"
    "Cvar.h"
    "GlobalCtx2.cpp"
    "GlobalCtx2.h"
    "LUSMacros.h"
    "Window.cpp"
    "Window.h"
    "WindowShim.cpp"
    "WindowShim.h"
)
source_group("Source Files\\Globals" FILES ${Source_Files__Globals})

set(Source_Files__Lib
    "Lib/mINI/src/mini/ini.h"
    "Lib/StrHash64.cpp"
    "Lib/StrHash64.h"
    "Lib/tinyxml2/tinyxml2.cpp"
    "stox.cpp"
    "stox.h"
)
source_group("Source Files\\Lib" FILES ${Source_Files__Lib})

set(Source_Files__Lib__Fast3D
    "Lib/Fast3D/gfx_cc.cpp"
    "Lib/Fast3D/gfx_cc.h"
    "Lib/Fast3D/gfx_opengl.cpp"
    "Lib/Fast3D/gfx_opengl.h"
    "Lib/Fast3D/gfx_pc.cpp"
    "Lib/Fast3D/gfx_pc.h"
    "Lib/Fast3D/gfx_rendering_api.h"
    "Lib/Fast3D/gfx_screen_config.h"
    "Lib/Fast3D/gfx_sdl.h"
    "Lib/Fast3D/gfx_sdl2.cpp"
    "Lib/Fast3D/gfx_window_manager_api.h"
)
source_group("Source Files\\Lib\\Fast3D" FILES ${Source_Files__Lib__Fast3D})

if (CMAKE_SYSTEM_NAME STREQUAL "Windows")
set(Source_Files__Lib__Fast3D__extra
    "Lib/Fast3D/gfx_direct3d11.cpp"
    "Lib/Fast3D/gfx_direct3d11.h"
    "Lib/Fast3D/gfx_direct3d12.cpp"
    "Lib/Fast3D/gfx_direct3d12.h"
    "Lib/Fast3D/gfx_direct3d12_guids.h"
    "Lib/Fast3D/gfx_direct3d_common.cpp"
    "Lib/Fast3D/gfx_direct3d_common.h"
    "Lib/Fast3D/gfx_dxgi.cpp"
    "Lib/Fast3D/gfx_dxgi.h"
)
elseif (CMAKE_SYSTEM_NAME STREQUAL "Linux")
set(Source_Files__Lib__Fast3D__extra
    "Lib/Fast3D/gfx_glx.cpp"
    "Lib/Fast3D/gfx_glx.h"
)
endif()
source_group("Source Files\\Lib\\Fast3D\\extra" FILES ${Source_Files__Lib__Fast3D__extra})

set(Source_Files__Lib__ImGui
    "Lib/ImGui/backends/imgui_impl_opengl3.cpp"
    "Lib/ImGui/backends/imgui_impl_opengl3.h"
    "Lib/ImGui/backends/imgui_impl_sdl.cpp"
    "Lib/ImGui/backends/imgui_impl_sdl.h"
    "Lib/ImGui/imconfig.h"
    "Lib/ImGui/imgui.cpp"
    "Lib/ImGui/imgui.h"
    "Lib/ImGui/imgui_demo.cpp"
    "Lib/ImGui/imgui_draw.cpp"
    "Lib/ImGui/imgui_internal.h"
    "Lib/ImGui/imgui_tables.cpp"
    "Lib/ImGui/imgui_widgets.cpp"
    "Lib/ImGui/imstb_rectpack.h"
    "Lib/ImGui/imstb_textedit.h"
    "Lib/ImGui/imstb_truetype.h"
)
if (CMAKE_SYSTEM_NAME STREQUAL "Windows")
set(Source_Files__Lib__ImGui__Windows
    "Lib/ImGui/backends/imgui_impl_dx11.cpp"
    "Lib/ImGui/backends/imgui_impl_dx11.h"
    "Lib/ImGui/backends/imgui_impl_win32.cpp"
    "Lib/ImGui/backends/imgui_impl_win32.h"
)
endif ()
source_group("Source Files\\Lib\\ImGui" FILES ${Source_Files__Lib__ImGui} ${Source_Files__Lib__ImGui__Windows})

set(Source_Files__Lib__Mercury
    "Lib/Mercury/Mercury.cpp"
    "Lib/Mercury/Mercury.h"
)
source_group("Source Files\\Lib\\Mercury" FILES ${Source_Files__Lib__Mercury})

set(Source_Files__Lib__stb
    "Lib/stb/stb_image.h"
    "Lib/stb/stb_image_write.h"
    "Lib/stb/stb_impl.c"
)
source_group("Source Files\\Lib\\stb" FILES ${Source_Files__Lib__stb})

set(Source_Files__Lib__dr_libs
    "Lib/dr_libs/mp3.h"
    "Lib/dr_libs/wav.h"
)
source_group("Source Files\\Lib\\dr_libs" FILES ${Source_Files__Lib__dr_libs})

set(Source_Files__Lib__tinyxml2
    "Lib/tinyxml2/tinyxml2.h"
)
source_group("Source Files\\Lib\\tinyxml2" FILES ${Source_Files__Lib__tinyxml2})

set(Source_Files__Logging
    "luslog.cpp"
    "luslog.h"
)
source_group("Source Files\\Logging" FILES ${Source_Files__Logging})

set(Source_Files__Resources
    "GameVersions.h"
    "Resource.cpp"
    "Resource.h"
    "ResourceMgr.cpp"
    "ResourceMgr.h"
)
source_group("Source Files\\Resources" FILES ${Source_Files__Resources})

set(Source_Files__Resources__Factories
    "Factories/AnimationFactory.cpp"
    "Factories/ArrayFactory.cpp"
    "Factories/AudioFactory.cpp"
    "Factories/BlobFactory.cpp"
    "Factories/CollisionHeaderFactory.cpp"
    "Factories/CutsceneFactory.cpp"
    "Factories/DisplayListFactory.cpp"
    "Factories/MaterialFactory.cpp"
    "Factories/MtxFactory.cpp"
    "Factories/PathFactory.cpp"
    "Factories/PlayerAnimationFactory.cpp"
    "Factories/ResourceLoader.cpp"
    "Factories/SceneFactory.cpp"
    "Factories/SkeletonFactory.cpp"
    "Factories/SkeletonLimbFactory.cpp"
    "Factories/TextFactory.cpp"
    "Factories/TextureFactory.cpp"
    "Factories/VtxFactory.cpp"
)
source_group("Source Files\\Resources\\Factories" FILES ${Source_Files__Resources__Factories})

set(Source_Files__Resources__Files
    "Animation.cpp"
    "Array.cpp"
    "Audio.cpp"
    "Blob.cpp"
    "CollisionHeader.cpp"
    "Cutscene.cpp"
    "DisplayList.cpp"
    "Material.cpp"
    "Matrix.cpp"
    "Model.cpp"
    "Path.cpp"
    "PlayerAnimation.cpp"
    "Scene.cpp"
    "Skeleton.cpp"
    "SkeletonLimb.cpp"
    "Text.cpp"
    "Texture.cpp"
    "Vertex.cpp"
)
source_group("Source Files\\Resources\\Files" FILES ${Source_Files__Resources__Files})

set(Source_Files__Resources__mpq
    "Archive.cpp"
    "Archive.h"
    "File.cpp"
    "File.h"
)
source_group("Source Files\\Resources\\mpq" FILES ${Source_Files__Resources__mpq})

if (CMAKE_SYSTEM_NAME STREQUAL "Darwin")
set(Source_Files__Darwin
    "OSXFolderManager.mm"
    "OSXFolderManager.h"
)
source_group("Source Files\\Darwin" FILES ${Source_Files__Darwin})
endif()

if (CMAKE_SYSTEM_NAME STREQUAL "NintendoSwitch")
set(Source_Files__NintendoSwitch
       "SwitchImpl.cpp"
       "SwitchImpl.h"
)
source_group("Source Files\\NintendoSwitch" FILES ${Source_Files__NintendoSwitch})
endif()

set(ALL_FILES
    ${Header_Files__Resources__Factories}
    ${Header_Files__Resources__Files}
    ${Source_Files__Audio}
    ${Source_Files__Audio__extra}
    ${Source_Files__Controller}
    ${Source_Files__Controller__Attachment}
    ${Source_Files__CustomImpl}
    ${Source_Files__CustomImpl__Hooks}
    ${Source_Files__CustomImpl__Utils}
    ${Source_Files__Globals}
    ${Source_Files__Lib}
    ${Source_Files__Lib__Fast3D}
    ${Source_Files__Lib__Fast3D__extra}
    ${Source_Files__Lib__ImGui}
    ${Source_Files__Lib__ImGui__Windows}
    ${Source_Files__Lib__Mercury}
    ${Source_Files__Lib__stb}
    ${Source_Files__Lib__dr_libs}
    ${Source_Files__Lib__tinyxml2}
    ${Source_Files__Logging}
    ${Source_Files__Resources}
    ${Source_Files__Resources__Factories}
    ${Source_Files__Resources__Files}
    ${Source_Files__Resources__mpq}
    ${Source_Files__Darwin}
    ${Source_Files__NintendoSwitch}
)

################################################################################
# Target
################################################################################
add_library(${PROJECT_NAME} STATIC ${ALL_FILES})

if (NOT TARGET storm)
    add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/../../StormLib ${CMAKE_BINARY_DIR}/StormLib EXCLUDE_FROM_ALL)
endif()

if (CMAKE_SYSTEM_NAME STREQUAL "Windows")
use_props(${PROJECT_NAME} "${CMAKE_CONFIGURATION_TYPES}" "${DEFAULT_CXX_PROPS}")
endif()

set(ROOT_NAMESPACE libultraship)

if (CMAKE_SYSTEM_NAME STREQUAL "Windows")
	set_target_properties(${PROJECT_NAME} PROPERTIES
		VS_GLOBAL_KEYWORD "Win32Proj"
	)
	if("${CMAKE_VS_PLATFORM_NAME}" STREQUAL "x64")
		set_target_properties(${PROJECT_NAME} PROPERTIES
			INTERPROCEDURAL_OPTIMIZATION_RELEASE "TRUE"
		)
	elseif("${CMAKE_VS_PLATFORM_NAME}" STREQUAL "Win32")
		set_target_properties(${PROJECT_NAME} PROPERTIES
			INTERPROCEDURAL_OPTIMIZATION_RELEASE "TRUE"
		)
	endif()
endif()
################################################################################
# MSVC runtime library
################################################################################
if (CMAKE_SYSTEM_NAME STREQUAL "Windows")
	get_property(MSVC_RUNTIME_LIBRARY_DEFAULT TARGET ${PROJECT_NAME} PROPERTY MSVC_RUNTIME_LIBRARY)
	if("${CMAKE_VS_PLATFORM_NAME}" STREQUAL "x64")
		string(CONCAT "MSVC_RUNTIME_LIBRARY_STR"
			$<$<CONFIG:Debug>:
				MultiThreadedDebug
			>
			$<$<CONFIG:Release>:
				MultiThreaded
			>
			$<$<NOT:$<OR:$<CONFIG:Debug>,$<CONFIG:Release>>>:${MSVC_RUNTIME_LIBRARY_DEFAULT}>
		)
	elseif("${CMAKE_VS_PLATFORM_NAME}" STREQUAL "Win32")
		string(CONCAT "MSVC_RUNTIME_LIBRARY_STR"
			$<$<CONFIG:Debug>:
				MultiThreadedDebug
			>
			$<$<CONFIG:Release>:
				MultiThreaded
			>
			$<$<NOT:$<OR:$<CONFIG:Debug>,$<CONFIG:Release>>>:${MSVC_RUNTIME_LIBRARY_DEFAULT}>
		)
	endif()
	set_target_properties(${PROJECT_NAME} PROPERTIES MSVC_RUNTIME_LIBRARY ${MSVC_RUNTIME_LIBRARY_STR})
endif()
################################################################################
# Compile definitions
################################################################################
if (CMAKE_SYSTEM_NAME STREQUAL "Windows")
	if("${CMAKE_VS_PLATFORM_NAME}" STREQUAL "x64")
		target_compile_definitions(${PROJECT_NAME} PRIVATE
			"$<$<CONFIG:Debug>:"
				"_DEBUG"
			">"
			"$<$<CONFIG:Release>:"
				"NDEBUG"
			">"
			"SPDLOG_ACTIVE_LEVEL=0;"
			"WIN32;"
			"_CONSOLE;"
			"_CRT_SECURE_NO_WARNINGS;"
			"ENABLE_DX11;"
			"ENABLE_OPENGL;"
			"%(PreprocessorDefinitions)GLEW_STATIC;"
			"UNICODE;"
			"_UNICODE"
			STORMLIB_NO_AUTO_LINK
		)
	elseif("${CMAKE_VS_PLATFORM_NAME}" STREQUAL "Win32")
		target_compile_definitions(${PROJECT_NAME} PRIVATE
			"$<$<CONFIG:Debug>:"
				"_DEBUG"
			">"
			"$<$<CONFIG:Release>:"
				"NDEBUG"
			">"
			"SPDLOG_ACTIVE_LEVEL=0;"
			"WIN32;"
			"_CONSOLE;"
			"_CRT_SECURE_NO_WARNINGS;"
			"ENABLE_OPENGL;"
			"ENABLE_DX11;"
			"%(PreprocessorDefinitions)GLEW_STATIC;"
			"UNICODE;"
			"_UNICODE"
			STORMLIB_NO_AUTO_LINK
		)
	endif()
endif()

if ("${CMAKE_CXX_COMPILER_ID}" MATCHES "GNU|Clang|AppleClang")
	target_compile_definitions(${PROJECT_NAME} PRIVATE
		"$<$<CONFIG:Debug>:"
				"_DEBUG"
			">"
			"$<$<CONFIG:Release>:"
				"NDEBUG"
			">"
			"ENABLE_OPENGL;"
            "SPDLOG_ACTIVE_LEVEL=0;"
	)
endif()
################################################################################
# Compile and link options
################################################################################
if (NOT CMAKE_SYSTEM_NAME MATCHES "Windows|NintendoSwitch")
    find_package(SDL2)
    if (USE_X11)
        find_package(X11)
    endif()
    if (NOT NO_GLEW)
        find_package(GLEW)

        if (NOT GLEW_FOUND)
            if (NOT CMAKE_SYSTEM_NAME MATCHES "Windows|Darwin")
                include (FetchContent)
                FetchContent_Declare(
                    glew
                    GIT_REPOSITORY https://github.com/Perlmint/glew-cmake.git
                    SOURCE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/../../external/glew
                )
                FetchContent_MakeAvailable(glew)
                add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/../../external/glew/build/cmake ${CMAKE_BINARY_DIR}/glew EXCLUDE_FROM_ALL)
            endif()
        endif()
    endif()

    if (NOT GLEW_FOUND)
       set(GLEW-INCLUDE ${CMAKE_CURRENT_SOURCE_DIR}/../../external/glew/include)
    else()
        set(GLEW-INCLUDE  ${GLEW_INCLUDE_DIRS})
    endif()
    set(SDL2-INCLUDE ${SDL2_INCLUDE_DIRS})
elseif (CMAKE_SYSTEM_NAME MATCHES "NintendoSwitch")
    find_package(SDL2)
else()
    set(GLEW-INCLUDE ${CMAKE_CURRENT_SOURCE_DIR}/Lib/GLEW/)
    set(SDL2-INCLUDE ${CMAKE_CURRENT_SOURCE_DIR}/Lib/SDL/)
endif()

target_include_directories(${PROJECT_NAME} PRIVATE
	${CMAKE_CURRENT_SOURCE_DIR}/Lib/spdlog/include/
	${CMAKE_CURRENT_SOURCE_DIR}/Lib/Fast3D/U64/
	${CMAKE_CURRENT_SOURCE_DIR}/Lib/Fast3D/U64/PR
	${SDL2-INCLUDE}
	${GLEW-INCLUDE}
	${SWITCH-INCLUDE}
	${CMAKE_CURRENT_SOURCE_DIR}/Lib/ImGui/
	${CMAKE_CURRENT_SOURCE_DIR}/../../ZAPDTR/ZAPDUtils
	${CMAKE_CURRENT_SOURCE_DIR}/../../StormLib/src
	.
	)

if(MSVC)
    if("${CMAKE_VS_PLATFORM_NAME}" STREQUAL "x64")
        target_compile_options(${PROJECT_NAME} PRIVATE
            $<$<CONFIG:Release>:
                /std:c++latest;
                /Oi;
                /Gy
            >
            /permissive-;
            /MP;
            /sdl;
            /W3;
            ${DEFAULT_CXX_DEBUG_INFORMATION_FORMAT};
            ${DEFAULT_CXX_EXCEPTION_HANDLING}
        )
    elseif("${CMAKE_VS_PLATFORM_NAME}" STREQUAL "Win32")
        target_compile_options(${PROJECT_NAME} PRIVATE
            $<$<CONFIG:Debug>:
                /Od;
                /Oi-;
                /W2
            >
            $<$<CONFIG:Release>:
                /Oi;
                /Gy;
                /W3
            >
            /permissive-;
            /MP;
            /sdl;
            ${DEFAULT_CXX_DEBUG_INFORMATION_FORMAT};
            ${DEFAULT_CXX_EXCEPTION_HANDLING}
        )
    endif()
    if("${CMAKE_VS_PLATFORM_NAME}" STREQUAL "x64")
        target_link_options(${PROJECT_NAME} PRIVATE
            $<$<CONFIG:Release>:
                /OPT:REF;
                /OPT:ICF
            >
            /SUBSYSTEM:CONSOLE
        )
    elseif("${CMAKE_VS_PLATFORM_NAME}" STREQUAL "Win32")
        target_link_options(${PROJECT_NAME} PRIVATE
            $<$<CONFIG:Release>:
                /OPT:REF;
                /OPT:ICF
            >
            /SUBSYSTEM:CONSOLE
        )
    endif()
endif()

if ("${CMAKE_CXX_COMPILER_ID}" STREQUAL "GNU")
	target_compile_options(${PROJECT_NAME} PRIVATE
		-Wall
		-Wextra
		-Wno-error
		-Wno-unused-variable
		-Wno-unused-parameter
		-Wno-unused-function
		-Wno-parentheses
		-Wno-narrowing
		-Wno-missing-field-initializers
	)
endif()
################################################################################
# Dependencies
################################################################################
# Link with other targets.

cmake_dependent_option(NO_GLEW "Build without using libGLEW" OFF "CMAKE_SYSTEM_NAME STREQUAL Linux" OFF)
cmake_dependent_option(NO_GLEW "Build without PulseAudio, using only SDLAudio" OFF "CMAKE_SYSTEM_NAME STREQUAL Linux" OFF)
cmake_dependent_option(USE_OPENGLES "Build targetting OpenGLESv2 instead of full OpenGL" OFF "CMAKE_SYSTEM_NAME STREQUAL Linux" OFF)
cmake_dependent_option(USE_X11 "Build with X11/GLX support" ON "CMAKE_SYSTEM_NAME STREQUAL Linux" OFF)

find_package(OpenGL QUIET)

if (CMAKE_SYSTEM_NAME STREQUAL "Linux")
    if (USE_X11)
        find_package(X11)
        add_compile_definitions(X11_SUPPORTED)
        set(GLX-LIB ${OPENGL_glx_LIBRARY})
        set(X11-LIBS ${X11_LIBRARIES})
    else()
        message(STATUS "Disabling X11/GLX")
    endif()

    if (NOT NO_PULSE)
        find_package(PulseAudio)
        set(PULSE-LIB ${PULSEAUDIO_LIBRARY})
    else()
        add_compile_definitions(NO_PULSE)
        message(STATUS "Disabling Pulse")
    endif()
endif()

if (NOT NO_GLEW)
    if (NOT GLEW_FOUND)
        set(GLEW-LIB glew_s)
    else()
        set(GLEW-LIB  GLEW::GLEW)
    endif()
else()
    message(STATUS "Disabling GLEW")
    add_compile_definitions(NO_GLEW)
endif()

if (USE_OPENGLES)
    add_compile_definitions(USE_OPENGLES IMGUI_IMPL_OPENGL_ES3)
    find_library(OPENGL-LIB GLESv2)
    if (NOT OPENGL-LIB)
        message(FATAL_ERROR "USE_OPENGLES=ON, but libGLESv2 could not be found")
    endif()
    message(STATUS "Building with OpenGLESv2")
else()
    set(OPENGL-LIB ${OPENGL_opengl_LIBRARY})
endif()

if (CMAKE_SYSTEM_NAME STREQUAL "Windows")
    if("${CMAKE_VS_PLATFORM_NAME}" STREQUAL "x64")
        target_link_libraries(${PROJECT_NAME}
            "glew32s;"
            "opengl32;"
            "storm;"
        )
    elseif("${CMAKE_VS_PLATFORM_NAME}" STREQUAL "Win32")
        target_link_libraries(${PROJECT_NAME}
            "glew32s;"
            "opengl32;"
            "storm;"
        )
    endif()
elseif(CMAKE_SYSTEM_NAME STREQUAL "Darwin")
    find_package(SDL2)
    find_package(GLEW)
    find_package(OpenGL QUIET)
    find_Library(OSX_FOUNDATION Foundation)
    set(THREADS_PREFER_PTHREAD_FLAG ON)
    find_package(Threads REQUIRED)
    target_link_libraries(${PROJECT_NAME}
       "storm;"
        SDL2::SDL2
        GLEW::GLEW
        ${OPENGL_opengl_LIBRARY}
        ${CMAKE_DL_LIBS}
        Threads::Threads
	${OSX_FOUNDATION}
    )
elseif(CMAKE_SYSTEM_NAME STREQUAL "NintendoSwitch")
    set(THREADS_PREFER_PTHREAD_FLAG ON)
    find_package(Threads REQUIRED)
    target_link_libraries(${PROJECT_NAME}
        storm
        SDL2::SDL2
        Threads::Threads
    )
else()
    target_link_libraries(${PROJECT_NAME}
        SDL2::SDL2
        ${PULSE-LIB}
        ${GLEW-LIB}
        ${GLX-LIB}
        ${OPENGL-LIB}
        ${X11-LIBS}
        storm
    )
endif()

if (CMAKE_SYSTEM_NAME STREQUAL "Windows")
    if("${CMAKE_VS_PLATFORM_NAME}" STREQUAL "x64")
        add_library(glew32s STATIC IMPORTED )
        set_property(TARGET glew32s PROPERTY
            IMPORTED_LOCATION ${CMAKE_CURRENT_SOURCE_DIR}/Lib/GLEW/x64/glew32s.lib  )
        set_property(TARGET glew32s PROPERTY
            IMPORTED_IMPLIB ${CMAKE_CURRENT_SOURCE_DIR}/Lib/GLEW/x64/glew32s.lib)
    elseif("${CMAKE_VS_PLATFORM_NAME}" STREQUAL "Win32")
        add_library(glew32s STATIC IMPORTED )
        set_property(TARGET glew32s PROPERTY
            IMPORTED_LOCATION ${CMAKE_CURRENT_SOURCE_DIR}/Lib/GLEW/x86/glew32s.lib  )
        set_property(TARGET glew32s PROPERTY
            IMPORTED_IMPLIB ${CMAKE_CURRENT_SOURCE_DIR}/Lib/GLEW/x86/glew32s.lib)
    endif()
endif()
