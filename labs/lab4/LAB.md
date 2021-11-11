# Laboratório 4
---------------

## Crie um teste para execução e validação do imagem

No laboratório 4, iremos criar um teste simples utilizando *OpenEmbedded selftests* como referência. Existe outras formas de testar seu *build*, utilizando outras ferramentas inclusive. Mas nesse exemplo, iremos utilizar essa ferramenta em específico. Os testes são basicamente desenvolvidos em Python utilizando `unittest`.

Ainda utilizando a *layer* criada no laboratório 2. Para isso, crie os diretórios necessários.

    $ mkdir -p ../meta-sel/lib/oeqa/

Vamos criar o arquivo de teste da aplicação `sl`.

    $ vim ../meta-sel/lib/oeqa/sl.py
    
E adicionar o conteúdo.

```python
#
# SPDX-License-Identifier: GPLv3
#

from oeqa.runtime.case import OERuntimeTestCase
from oeqa.core.decorator.depends import OETestDepends


class SLTest(OERuntimeTestCase):
    
    @OETestDepends(['ssh.SSHTest.test_ssh'])
    def test_df(self):
        cmd = "[[ -f /usr/bin/sl ]]"
        (status,output) = self.target.run(cmd)
        msg = 'SL was not found'
        self.assertEqual(int(status), 0, msg=msg)
```
            
Agora, vamos verificar se nosso teste está disponível.


Por fim, vamos executá-lo.

    $ oe-selftest --run-tests-by name SLTest
    
Sucesso ou falha?
