#kotlin 

Определяет поведение для всех необработанных корутин в данном CoroutineContext.
Выполняется в последнюю очередь после того, как была вызвана ошибка. 
Может быть вызван в любом потоке 

Никак не влияет на исполнение корутин, то есть является скорее side эффектом, и если мы не обработаем ошибку в try catch, мы упадем с крашем, даже если есть Exception Handler