from building import *
import rtconfig
Import('RTT_ROOT')

cwd = GetCurrentDir()
src = Glob('mbedtls/library/*.c')
SrcRemove(src, 'net_sockets.c')

src += Glob('mbedtls-port/src/*.c')

if GetDepend(['PKG_USING_MBEDTLS_EXAMPLE']):
    src += Glob('examples/*.c')
    
CPPPATH = [
cwd,
cwd + '/mbedtls/include',
cwd + '/mbedtls/include/mbedtls',
cwd + '/mbedtls-port/inc',
]
CPPPATH += [RTT_ROOT + '/include/libc']

if rtconfig.CROSS_TOOL == 'gcc' :
    CPPDEFINES = ['MBEDTLS_CONFIG_FILE=\\"tls_config.h\\"']
elif rtconfig.CROSS_TOOL == 'keil':
    CPPDEFINES = ['MBEDTLS_CONFIG_FILE=\\"tls_config.h\\"']
else:
    CPPDEFINES = []

group = DefineGroup('mbedtls', src, depend = ['PKG_USING_MBEDTLS'], CPPPATH = CPPPATH, CPPDEFINES = CPPDEFINES)

Return('group')
