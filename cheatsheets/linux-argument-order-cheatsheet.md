Linux Command Argument Order Cheat Sheet

CommandSyntaxExamplechownchown USER FILEchown researcher9 project\_r.txtchmodchmod PERMISSIONS FILEchmod g-x draftsmvmv SOURCE DESTINATIONmv file.txt reports/cpcp SOURCE DESTINATIONcp file.txt backup/rmrm FILErm tempnotes.txtmkdirmkdir DIRNAMEmkdir tryhackmecdcd DIRNAMEcd Security-Portfoliogrepgrep PATTERN FILEgrep "error" logs.txtcatcat FILEcat notes.txttouchtouch FILEtouch notes.mduseradduseradd USERuseradd researcher9usermod -gusermod -g GROUP USERusermod -g research\_team researcher9usermod -a -Gusermod -a -G GROUP USERusermod -a -G sales\_team researcher9groupdelgroupdel GROUPgroupdel researcher9git addgit add FILEgit add .git commitgit commit -m "MESSAGE"git commit -m "Add file"git pushgit push REMOTE BRANCHgit push origin maingit clonegit clone URLgit clone https://github.com/...



The Patterns to Remember

USER comes last:



usermod always — usermod -g GROUP USER



SOURCE before DESTINATION:



mv, cp always — think "from → to"



PERMISSIONS before FILE:



chmod always — chmod g-x FILE



USER before FILE:



chown always — chown USER FILE

