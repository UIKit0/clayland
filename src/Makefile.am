bin_PROGRAMS = clayland

INCLUDES = \
	@CLUTTER_CFLAGS@ \
	@COGL_CFLAGS@ \
	-DXWAYLAND_PATH='"@XWAYLAND_PATH@"'

clayland_SOURCES = \
	clayland.c \
	clayland-compositor.h \
	clayland-data-device.c \
	clayland-data-device.h \
	clayland-keyboard.c \
	clayland-keyboard.h \
	clayland-pointer.c \
	clayland-pointer.h \
	clayland-seat.c \
	clayland-seat.h \
	xserver-protocol.c \
	xserver-server-protocol.h \
	$(NULL)

clayland.c : xserver-server-protocol.h

clayland_LDADD = \
	@CLUTTER_LIBS@ \
	@COGL_LIBS@

%-protocol.c : @WAYLAND_EXTENSION_PROTOCOLS_DIR@/%.xml
	$(AM_V_GEN)$(WAYLAND_SCANNER) code < $< > $@
%-server-protocol.h : @WAYLAND_EXTENSION_PROTOCOLS_DIR@/%.xml
	$(AM_V_GEN)$(WAYLAND_SCANNER) server-header < $< > $@
%-client-protocol.h : @WAYLAND_EXTENSION_PROTOCOLS_DIR@/%.xml'
	$(AM_V_GEN)$(WAYLAND_SCANNER) client-header < $< > $@
