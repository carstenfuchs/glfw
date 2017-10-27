import os, sys

Import('env')


envGLFW = env.Clone()

source_files = Split("context.c init.c input.c monitor.c vulkan.c window.c")

if sys.platform == "win32":
    envGLFW.Append(CPPDEFINES=['_GLFW_WIN32'])
    source_files += Split(
        "win32_init.c win32_joystick.c win32_monitor.c win32_time.c "
        "win32_tls.c win32_window.c wgl_context.c egl_context.c"
    )

elif sys.platform.startswith("linux"):
    envGLFW.Append(CPPDEFINES=['_GLFW_X11', '_GLFW_HAS_XF86VM'])
    source_files += Split(
        "x11_init.c x11_monitor.c x11_window.c xkb_unicode.c linux_joystick.c "
        "posix_time.c posix_tls.c glx_context.c egl_context.c"
    )

elif sys.platform == "Cocoa":   # for now, this is just a reminder
    envGLFW.Append(CPPDEFINES=['_GLFW_COCOA', '_GLFW_USE_CHDIR', '_GLFW_USE_MENUBAR', '_GLFW_USE_RETINA'])


envGLFW.StaticLibrary(
    "glfw",
    source=["src/" + sf for sf in source_files]
)
