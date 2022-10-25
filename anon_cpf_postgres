CREATE OR REPLACE FUNCTION public.anon_cpf_cnpj(p_cpf character varying)
 RETURNS varchar
 LANGUAGE plpgsql
AS $function$
declare
    
begin

    if (p_cpf ~* '^([0-9]{11})$')
    then 
        return concat(substring(p_cpf,0,4),'*****',substring(p_cpf,9,3));
    end if;

    if (p_cpf ~* '^([0-9]{3}\.[0-9]{3}\.[0-9]{3}\-[0-9]{2})$')
    then 
        return concat(substring(p_cpf,0,4),'.***.**',substring(p_cpf,11,4));
    end if;
   
    if (p_cpf ~* '^([0-9]{14})$')
    then 
        return concat(substring(p_cpf,0,4),'********',substring(p_cpf,12,3));
    end if;

    if (p_cpf ~* '^([0-9]{2}\.[0-9]{3}\.[0-9]{3}\/[0-9]{4}\-[0-9]{2})$')
    then 
        return concat(substring(p_cpf,0,5),'**.***/***',substring(p_cpf,15,4));
    end if;

   if (not (p_cpf ~* '^([0-9]{11})$' or p_cpf ~* '^([0-9]{3}\.[0-9]{3}\.[0-9]{3}\-[0-9]{2})$' or p_cpf ~* '^([0-9]{14})$' or p_cpf ~* '^([0-9]{2}\.[0-9]{3}\.[0-9]{3}\/[0-9]{4}\-[0-9]{2})$' ) ) 
    then
        return concat(substring(p_cpf,0,4),'********');  
    end if;
    
end;
$function$
;
