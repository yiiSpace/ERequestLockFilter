ERequestLockFilter
==================

yii extension (based yii1.x) for preventing unintentionally posting data with ajax request twice or more.


##  usage example :

in your controller :
~~~
    public function filters()
    {
        return array(
            array(
                'my.filters.ERequestLockFilter',
                // 'method'=>'ANY',
            ),
        );
    }

~~~

or you want apply the filter for the controllers under some module , then in the XxxModule :
~~~
  public function beforeControllerAction($controller, $action)
    {
        if(parent::beforeControllerAction($controller, $action))
        {
            /**
             * here you can do the filtering manually according to the [controller or action]
             *  eg :
             *       if($controller->id == 'xxx' && $action->id = 'yyy'){...}
             */
            $filterChan = CFilterChain::create($controller,$action,array(
                array(
                    'my.filters.ERequestLockFilter',
                    // 'method'=>'ANY',
                ),
            ));
            $filterChan->run() ;

            // above code have made the controller and the action been executed  so we just return a false to halt the
            // execution !
            return false ;
        }
        else
            return false;
    }

~~~

##  the available options :

 -  please read the source code ^-^

