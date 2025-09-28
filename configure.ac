# configure.ac: Autoconf template for zfs-rpms.  -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.69])
AC_INIT([zfs-rpms], [1.0.0], [])
AM_INIT_AUTOMAKE([foreign])

HOME_PREFIX=${HOME}/bin${PATH_SEPARATOR}
ASDF_PREFIX=${HOME}/.asdf/shims${PATH_SEPARATOR}
LOCAL_PREFIX=/usr/local/sbin${PATH_SEPARATOR}/usr/local/bin${PATH_SEPARATOR}

AC_MSG_CHECKING([whether to search optional path])
AC_ARG_WITH([opt-path],
  [AS_HELP_STRING([--with-opt-path@<:@=PATH@:>@],
    [search optional PATH @{:@default: /opt/local/bin@:}@])],
  [], [with_opt_path=check])
if test ."$with_opt_path" = .'yes' || test ."$with_opt_path" = .'check'; then
    if test -d /opt/local/bin; then
        OPT_PREFIX=/opt/local/sbin${PATH_SEPARATOR}/opt/local/bin
    fi
elif test ! ."$with_opt_path" = .'no'; then
    if test -d "$with_opt_path"; then
        OPT_PREFIX=${with_opt_path}
    else
        AC_MSG_WARN([${with_opt_path}: No such file or directory])
    fi
fi
AC_MSG_RESULT([${OPT_PREFIX:-no}])
OPT_PATHS=$(echo "$OPT_PREFIX" | tr "${PATH_SEPARATOR}" ' ')
AC_SUBST([OPT_PATHS], ["$OPT_PATHS"])
OPT_PREFIX=${OPT_PREFIX:+"${OPT_PREFIX}${PATH_SEPARATOR}"}

# Checks for programs.
AC_PATH_PROG([ASDF_CMD],        [asdf],               [], [${HOME_PREFIX}${PATH}])

AC_PATH_PROGS([CAT_CMD],        [gcat cat],           [], [${OPT_PREFIX}${PATH}])

AC_PATH_PROG([CMAKE_CMD],       [cmake],              [], [${OPT_PREFIX}${PATH}])
AC_PATH_PROG([CURL_CMD],        [curl],               [], [${OPT_PREFIX}${PATH}])

AC_PATH_PROGS([DNF_CMD],        [dnf5 dnf])

AC_PATH_PROG([ED_CMD],          [ed],                 [], [${LOCAL_PREFIX}${PATH}])
AC_PATH_PROG([GIT_CMD],         [git],                [], [${OPT_PREFIX}${PATH}])

AC_PATH_PROGS([GREP_CMD],       [ggrep grep],         [], [${OPT_PREFIX}${PATH}])
AC_PATH_PROGS([HEAD_CMD],       [ghead head],         [], [${OPT_PREFIX}${PATH}])

AC_PATH_PROGS([HTMLQ_CMD],      [htmlq],              [], [${ASDF_PREFIX}${PATH}])

AC_PATH_PROGS([MAKE_CMD],       [gmake make],         [], [${OPT_PREFIX}${PATH}])
AC_PATH_PROGS([MKDIR_CMD],      [gmkdir mkdir],       [], [${OPT_PREFIX}${PATH}])

AC_PATH_PROG([PATCH_CMD],       [patch],              [], [${OPT_PREFIX}${PATH}])
AC_PATH_PROG([PIP_CMD],         [pip],                [], [${ASDF_PREFIX}${PATH}])

AC_PATH_PROGS([READLINK_CMD],   [greadlink readlink], [], [${OPT_PREFIX}${PATH}])
AC_PATH_PROGS([RM_CMD],         [grm rm],             [], [${OPT_PREFIX}${PATH}])

AC_PATH_PROG([RPM_CMD],         [rpm],                [], [${OPT_PREFIX}${PATH}])

AC_PATH_PROGS([SORT_CMD],       [gsort sort],         [], [${OPT_PREFIX}${PATH}])

AC_PATH_PROG([SUDO_CMD],        [sudo],               [], [${OPT_PREFIX}${PATH}])

AC_PATH_PROGS([TAIL_CMD],       [gtail tail],         [], [${OPT_PREFIX}${PATH}])
AC_PATH_PROGS([TAR_CMD],        [gtar tar],           [], [${OPT_PREFIX}${PATH}])
AC_PATH_PROGS([TEE_CMD],        [gtee tee],           [], [${OPT_PREFIX}${PATH}])

AC_PATH_PROG([UNAME_CMD],       [uname],              [], [${OPT_PREFIX}${PATH}])

AC_CONFIG_FILES([Makefile])
AC_CONFIG_FILES([build-llama.cpp-cuda],               [chmod +x build-llama.cpp-cuda])
AC_CONFIG_FILES([install-llama.cpp-cuda],             [chmod +x install-llama.cpp-cuda])
AC_CONFIG_FILES([install-asdf],                       [chmod +x install-asdf])
AC_CONFIG_FILES([install-intel-oneapi-hpc],           [chmod +x install-intel-oneapi-hpc])
AC_CONFIG_FILES([install-nvidia-cuda],                [chmod +x install-nvidia-cuda])

AC_OUTPUT
