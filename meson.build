project('musl-fts', 'c',
	version: '1.2.7',
	default_options: 'default_library=both')

fts_source = files([
	'fts.c',
])

install_headers('fts.h')

conf_data = configuration_data()

cc = meson.get_compiler('c')

#conf_data.set('HAVE_CONFIG_H', true)

# check_header
conf_data.set('HAVE_ASSERT_H', cc.has_header('assert.h'))
conf_data.set('HAVE_DIRENT_H', cc.has_header('dirent.h'))
conf_data.set('HAVE_ERRNO_H', cc.has_header('errno.h'))
conf_data.set('HAVE_FCNTL_H', cc.has_header('fcntl.h'))
conf_data.set('HAVE_STDLIB_H', cc.has_header('stdlib.h'))
conf_data.set('HAVE_STRING_H', cc.has_header('string.h'))
conf_data.set('HAVE_UNISTD_H', cc.has_header('unistd.h'))
conf_data.set('HAVE_SYS_PARAM_H', cc.has_header('sys/param.h'))
conf_data.set('HAVE_SYS_STAT_H', cc.has_header('sys/stat.h'))

# these 2 required a value 0 or 1
conf_data.set10('HAVE_DECL_MAX', cc.has_header_symbol('sys/param.h', 'MAX'))
conf_data.set10('HAVE_DECL_UINTMAX_MAX', cc.has_header_symbol('limits.h', 'UINTMAX_MAX'))

conf_data.set('HAVE_DIRFD', cc.has_function('dirfd'))
conf_data.set('HAVE_DIR_DD_FD', cc.has_members('DIR', 'dd_fd', prefix: '''#include <sys/types.h>
#include <dirent.h>'''))
conf_data.set('HAVE_DIR_D_FD', cc.has_members('DIR', 'd_fd', prefix: '''#include <sys/types.h>
#include <dirent.h>'''))

configure_file(output : 'config.h',
               configuration : conf_data)

add_project_arguments('-DHAVE_CONFIG_H=1', language : 'c')

ftslib = library('fts',
	fts_source,
	include_directories : '.',
	install : true
)

# musl-fts.pc
pkg = import('pkgconfig')
pkg.generate(ftslib,
  name: 'musl-fts',
  filebase: 'musl-fts',
  description: 'Implementation of fts(3) functions for musl libc',
  version: meson.project_version())
