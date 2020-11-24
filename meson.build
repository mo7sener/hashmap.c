project('hashmap', 'c')

hashmap_src = files('hashmap.c')
hashmap_inc = include_directories('.')

hashmap_lib = library('hashmap', 
  hashmap_src, 
  include_directories: hashmap_inc
)

hashmap_exe = executable('hashmap', 
  hashmap_src, 
  include_directories: hashmap_inc,
  c_args: '-DHASHMAP_TEST',
)

hashmap_dep = declare_dependency(
  link_with: hashmap_lib,
  include_directories: hashmap_inc,
)

if meson.version().version_compare('>= 0.54.0')
  meson.override_dependency('hashmap', hashmap_dep)
endif

test('test', hashmap_exe)
test('bench', hashmap_exe, env: ['BENCH=1'])