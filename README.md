# Proj2-S.O-B

O projeto consiste em modificar o módulo de kernel que implementa o sistema de arquivos minix
em sistemas operacionais Linux, de forma que os arquivos dos usuários sejam armazenados de
maneira cifrada.
Ao carregar o módulo de kernel modificado, deve-se informar no parâmetro key a chave simétrica
que será usada para cifrar e decifrar o conteúdo dos arquivos. A chave simétrica corresponde a
uma string representada em hexadecimal (cada byte corresponde a dois dígitos hexa). A carga do
módulo deve ser executada como no exemplo a seguir:
insmod minix.ko key=”0123456789ABCDEF”
Para testar o funcionamento do módulo modificado, deve ser realizada a carga do módulo e criada
uma nova partição em seu sistema que será formatada usando-se o sistema de arquivos minix
modificado através do comando mkfs.minix.
Todos os arquivos armazenados nesta partição deverão ser cifrados pelo módulo minix no
momento de sua criação ou atualização utilizando o algoritmo AES com a chave fornecida durante
a carga do módulo.
Durante a leitura de um arquivo armazenado nesta partição, o conteúdo do arquivo deve ser
decifrado pelo módulo minix utilizando o algoritmo AES em modo ECB com a chave fornecida
durante a carga do módulo.
Repare que o processo de cifragem dos arquivos será transparente para os programas em espaço
de usuário. Isso significa que ao gravar um arquivo no sistema de arquivos utilizando o módulo
minix modificado, o conteúdo do arquivo será armazenado cifrado, mas ao ler o arquivo o
conteúdo retornado será o conteúdo já decifrado.
Para verificar se o processo de cifragem dos dados está sendo de fato realizado, o módulo minix
modificado deve ser descarregado e o módulo minix original presente no kernel (sem
modificações) deve ser carregado. Neste caso, o conteúdo dos arquivos ainda estará acessível
aos programas de usuário, mas será diferente do conteúdo originalmente armazenado, pelo fato
de não ter sido realizada a decifragem do dados
