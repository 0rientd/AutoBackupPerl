#!/usr/bin/perl
#
# Versão 1.2
#
# Sobe a licença Artistic License 2.0
#
# USE, EDITE, COMPILE. MAS SEMPRE DISTRIBUA O CÓDIGO FONTE!
# CONHECIMENTO DEVE SER LIVRE E DE TODOS!
#
# CODED BY: HackerOrientado
#
# Me sigam no twitter -> @HackerOrientado
# Facebook -> facebook.com/profile.php?id=100009514835764
# Página Ciência Hacker -> facebook.com/CienciaHacker
# Grupo Ciência Hacker -> facebook.com/groups/cienciahacker/
# Página no Facebook do Inurl Brasil -> facebook.com/InurlBrasil
# Blog Inurl Brasil -> blog.inurl.com.br/
#
#

use strict;
use warnings;

my ( $autoBackupSH, $autoBackupPerl, $entrada, $nomeUSB, $nomePC, $pausa );

$autoBackupSH = '#!/bin/bash
### BEGIN INIT INFO
# Provides: AutoBackup.sh
# Required-Start: $local_fs $remote_fs $network $syslog
# Required-Stop: $local_fs $remote_fs $network $syslog
# Default-Start: 2 3 4 5
# Default-Stop: 0 1 6
# Short-Description: Inicia o script Perl no tempo de boot do sistema.
# Description: Permite a inicializacao do script Perl no inicio do boot.
### END INIT INFO

perl /etc/AutoBackup/AutoBackup.pl

exit 0
';

system "clear";

print "\t\t   Bem vindo ao installer do Auto Backup Perl\n\n\n";
print "* Este instalador ira te guiar e explicar todos os procedimentos aqui tomandos.\n\n";
print "Primeiro de tudo, voce precisa ter acesso root pois sera criado arquivos de configuracoes necessarios para a execucao dos scripts.\n";
print "Para ser mais claro, o script ira criar uma pasta e arquivos no diretorio '/etc/' onde requer acesso root.\n";
print "Por ser uma pasta onde todo OS tem e de facil localizacao, e o mais adequado para nao 'poluir' visualmente seu PC.\n\n\n";
print "Sem mais delongas... Voce e root ou deu permissao para este script\? [s|n]\n";
print "-> ";

$entrada = <STDIN>; chomp $entrada;

if ( $entrada !~ /[S,s]|[S,s]im/ ) {

  print "\n";
  print "Ok.. Pode voltar a executar o script novamente ^^\n";
  print "Nada foi criado ou alterado no seu sistema ^^\n";

  exit 0;

}

sleep 1;
system "clear";

print "Para comeco de tudo, o script funciona em segundo plano.\n";
print "Ele sempre sera iniciado com o sistema, mas por ser leve, nao ira comprometer o desempenho na inicializacao e nem no uso no seu dia-a-dia.\n";
print "Vamos la! :D\n\n";

print "Digite o nome do seu PC.\n";
print "O mesmo de quando voce instalou o OS e o mesmo que aparece no terminal.\n";
print "EX: pc-hackerorientado\@HackerOrientado-PC: -- Onde no caso o meu e o pc-hackerorientado\n";
print "-> ";

$nomePC = <STDIN>; chomp $nomePC;

sleep 1;
system "clear";

print "Agora sera criada uma pasta na area 'Documentos' em seu computador com o nome de AutoBackup.\n\n";
print "Esta sera a pasta onde tudo que tiver nela, sera copiado para o pendrive de forma automatica.\n";

system "mkdir /home/$nomePC/Documentos/AutoBackup/";
system "chmod 777 AutoBackup";

print "\n";
print "Pasta criada :D\n\n";

sleep 5;
system "clear";

print "Antes de continuar, me fale o nome do seu dispositivo USB.\n";
print "Aquele mesmo nome que aparece na hora de montar o USB ou quando voce conecta no computador.\n";
print "Estou trabalhando para automatizar isso... :/\n\n";
print "-> ";

$nomeUSB = <STDIN>; chomp $nomeUSB;

sleep 3;
system "clear";

print "Agora vou criar o arquivo chamado AutoBackup.sh e passar ele para a pasta /etc/init.d/\n\n";

open FILE, ">AutoBackup.sh" or die $!;
print FILE $autoBackupSH;
close FILE;

system "chmod 777 AutoBackup.sh";
system "mv AutoBackup.sh /etc/init.d/";
system "update-rc.d AutoBackup.sh defaults";

print "\n";
print "Arquivo de inicializacao criado com sucesso :D\n\n";

sleep 2;

print "Agora criarei a pasta e o arquivo na pasta /etc/ para que nao polua visualmente seu sistema\n";

$autoBackupPerl = "#!/usr/bin/perl

use strict;
use warnings;

sub main() {

  while (1) {

    if ( -e '/media/$nomePC/$nomeUSB/Backup/AutoBackup.config' ) {

      system 'cp -r /home/$nomePC/Documentos/AutoBackup /media/$nomePC/$nomeUSB/Backup/';

      last;

    }

  }

  sleep 3600;

  return main();

}

return main();

";

system "mkdir /etc/AutoBackup/";
system "chmod 777 /etc/AutoBackup/";

open FILE, ">AutoBackup.pl" or die $!;
print FILE $autoBackupPerl;
close FILE;

system "chmod 777 AutoBackup.pl";
system "mv AutoBackup.pl /etc/AutoBackup/";

sleep 1;
system "clear";

print "Pronto\!\n";
print "Falta so mais uma coisa.\n\n";

print "Criarei agora uma pasta chamada 'Backup' e nela ira conter um arquivo de 'configuracao'.\n\n";
print "Esta pasta sera muito importante e sem ela o script nao ira funcionar.\n\n";

system "mkdir Backup";
system "chmod 777 Backup";

system "touch AutoBackup.config";
system "chmod 777 AutoBackup.config";
system "mv AutoBackup.config Backup";

print "Copie esta pasta ( Backup ) para a raiz do seu pendrive e pronto\!\n";
print "Acabamos de instalar e configurar tudo.\n";
print "Para funcionar, reinicie o computador e conecte seu pendrive e aguarde poucos segundo dependendo da quantidade de arquivos na pasta AutoBackup e veja se funciona.\n\n";

print "O script e iniciado a cada inicializacao verificando o determinado pendrive conectado.\n";
print "Apos isso ele se auto inicia de hora em hora. Caso o pendrive esteja ainda conectado, ele ira fazer outro backup.\n\n";
print "Pode acontecer de o Linux demorar a desligar apos a instalacao.\n";
print "Espere cerca de 5 minutos e ele desligara normalmentem. Nao se preocupe.\n\n\n";
print "Qualquer bug, erro ou critica pode ser reportado a mim.\n";
print "E-mail -> hackerorientado\@protonmail.com\n\n";

#EoF
